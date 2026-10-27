---
name: motion
description: "Framer Motion (motion/react) system for React and Next.js. Shared duration/easing/spring tokens, reduced-motion and SSR rules, plus ready patterns for buttons, modals, toasts, stagger lists, page transitions, scroll reveals, layout animations, drag and swipe, text and number animation, SVG drawing, useAnimate sequences and loaders. Use whenever adding or reviewing animation in a React/Next.js project."
metadata:
  pricing: free
  cost: "Free (motion is MIT)."
  tags: [animation, framer-motion, react, nextjs]
---

# Motion

The motion layer for `dean-design-taste`. Motion must **guide attention, communicate state, or preserve spatial continuity**, or it gets removed. Responsiveness beats smoothness: an animation that delays input is worse than none.

- Standard UI patterns: [references/patterns.md](references/patterns.md)
- Gestures, text, SVG, sequences, loaders: [references/advanced.md](references/advanced.md)
- Long timelines, pinned/scrubbed scroll storytelling, SplitText or non-React pages: use the `gsap` skill instead (never both on one element).

## Rules

1. **Import from `motion/react`** (the `motion` package) in new code. `framer-motion` still works, and existing projects or blocks (e.g. Bencho) may use it, but never mix both in one tree.
2. **`"use client"`** on every file that uses motion components or hooks.
3. **Reduced motion overrides everything.** With `useReducedMotion()` true, drop transforms; allow only opacity fades of 0.2s or less. Loops stop.
4. **Animate `transform` and `opacity` only.** No `width`/`height`/`top`/`left`/`margin`/`padding` in `animate`. Use `scaleX`/`scaleY`, `x`/`y`, or `layout` for small shifts.
5. **Use the shared tokens and springs** below instead of inline durations and stiffness values, so the whole site moves with one personality.
6. **Exit with enter:** every `AnimatePresence` child has a stable `key` and an `exit`. Page transitions use `mode="wait"`.
7. **Scroll reveals run once** (`viewport={{ once: true }}`), with a stagger of 0.05–0.10s.
8. **Never read `window`/`navigator` at module level**; guard with `typeof window !== "undefined"`.
9. **Infinite animations pause** when `document.visibilityState === "hidden"`, and every listener or animation is cleaned up on unmount.
10. **Test drag and gestures on touch**, and combine offset and velocity thresholds for swipes.

## SSR and above-the-fold content

`motion` renders the `initial` styles in the server HTML, so `initial={{ opacity: 0 }}` doesn't cause a hydration mismatch. The real risk is **hiding content until JavaScript loads**, which hurts LCP and looks broken on slow devices. So:
- Don't fade in the hero headline, LCP image or primary CTA from `opacity: 0` on page load. Render them visible, or use `initial={false}`.
- Use entrance animations for below-the-fold content, in-view reveals and user-triggered state.

## Tokens and springs

```ts
// lib/motion-tokens.ts
export const motionTokens = {
  duration: {
    instant: 0.08,
    fast:    0.18,
    normal:  0.35,
    slow:    0.6,
    crawl:   1.0,
  },
  easing: {
    smooth: [0.22, 1, 0.36, 1],
    sharp:  [0.4, 0, 0.2, 1],
    bounce: [0.34, 1.56, 0.64, 1],
    linear: [0, 0, 1, 1],
  },
  distance: {
    xs: 4,
    sm: 8,
    md: 16,
    lg: 24,
    xl: 48,
  },
  scale: {
    subtle: 0.98,
    press:  0.95,
    pop:    1.04,
  },
}

export const springs = {
  snappy:  { type: "spring", stiffness: 300, damping: 30 },
  gentle:  { type: "spring", stiffness: 120, damping: 14 },
  bouncy:  { type: "spring", stiffness: 400, damping: 10 },
  instant: { type: "spring", stiffness: 600, damping: 35 },
  release: { type: "spring", stiffness: 200, damping: 20, restDelta: 0.001 },
}
```

### Runtime flags

```ts
// lib/motion-config.ts
export const motionConfig = {
  isLowEnd() {
    return (
      typeof navigator !== "undefined" &&
      navigator.hardwareConcurrency <= 4
    )
  },

  prefersReduced() {
    return (
      typeof window !== "undefined" &&
      window.matchMedia("(prefers-reduced-motion: reduce)").matches
    )
  },

  shouldAnimate({ essential = false } = {}) {
    if (this.prefersReduced()) return false
    if (!essential && this.isLowEnd()) return false
    return true
  },

  duration() {
    return this.isLowEnd() || this.prefersReduced()
      ? motionTokens.duration.instant
      : motionTokens.duration.normal
  },
}
```


| Duration | Use for |
| --- | --- |
| `instant` | tooltip, focus ring, badge |
| `fast` | button feedback, icon swap, toggle |
| `normal` | modal, card expand, element enter |
| `slow` | hero or section entrance, page transition |
| `crawl` | rare storytelling moments |

| Spring | Use for |
| --- | --- |
| `snappy` | default UI: buttons, chips, nav |
| `gentle` | cards, modals, panels |
| `bouncy` | playful moments only (empty states, onboarding) |
| `instant` | tooltips, popovers, dropdowns |
| `release` | drag release |

## Reduced-motion helper

```tsx
"use client"
import { useReducedMotion } from "motion/react"
import { motionTokens } from "@/lib/motion-tokens"

export function useSafeMotion(distance = motionTokens.distance.md) {
  const reduce = useReducedMotion()
  return {
    initial: { opacity: 0, y: reduce ? 0 : distance },
    animate: { opacity: 1, y: 0 },
    exit: { opacity: 0, y: reduce ? 0 : -distance },
  }
}
```

Low-end devices (`navigator.hardwareConcurrency <= 4`, checked client-side) can skip non-essential animation.

## Picking the API

| Situation | Use |
| --- | --- |
| Appear/disappear | `AnimatePresence` + `exit` |
| List entering in sequence | variants with `staggerChildren` |
| Route change | page-transition wrapper (`mode="wait"`, keyed by pathname) |
| Size or position change in place | `layout` (small subtrees only, up to ~5 children) |
| Same element across contexts | `layoutId` |
| Enter on scroll | `whileInView` + `viewport={{ once: true }}` |
| Value tied to scroll | `useScroll` + `useTransform` |
| Pointer-tracked smoothing | `useSpring` |
| Multi-step choreography | `useAnimate` with `async/await` |
| Drag, swipe, reorder | `drag`, `onDragEnd` thresholds, `Reorder.Group` |

## Anti-patterns

- Animating layout properties, or `layout` on long lists.
- `whileInView` without `once: true`; staggers over 0.1s.
- Modals without a focus trap, Escape to close, scroll lock, `role="dialog"` and `aria-modal`. Prefer Radix/React Aria dialogs and animate them.
- Bouncy springs on serious brands, or more than one "hero" animation per screen.
- Default purple/indigo accents in examples; use the project's tokens.
