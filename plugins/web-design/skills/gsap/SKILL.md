---
name: gsap
description: Use GSAP (GreenSock) for timeline choreography and scroll storytelling on websites - ScrollTrigger pinning and scrubbing, SplitText headline reveals, SVG drawing and morphing, Flip transitions, smooth scrolling - in React/Next.js (useGSAP) or plain HTML/Astro. Use when Dean wants scroll-driven sections, complex sequenced animations, text-splitting effects, SVG morphs, an award-style landing page, or mentions GSAP, ScrollTrigger or SplitText.
---

# GSAP

GSAP is free for commercial use, **all plugins included** (SplitText, MorphSVG, ScrollSmoother, DrawSVG, Inertia and the rest). It's not open source: it uses Webflow's "Standard No Charge" license. Don't use it to build a no-code visual animation tool that competes with Webflow, and don't strip its notices. Client sites, apps and AI-generated code are fine.

## GSAP or Motion?

| Use **`motion`** (Framer Motion) for | Use **GSAP** for |
| --- | --- |
| React UI state: hover, press, modals, toasts | Long timelines choreographing many elements |
| Layout and shared-element animation (`layout`, `layoutId`) | Scroll storytelling: pin sections, scrub timelines (ScrollTrigger) |
| Gestures, drag, reorder | SplitText line/word/char reveals |
| Enter/exit with `AnimatePresence` | SVG draw and morph, motion paths |
| | Non-React pages (Astro, plain HTML, `editorial-themes` sites) |

Both can live in one project, but **never animate the same element with both**.

## Setup (React / Next.js)

```bash
npm i gsap @gsap/react
```

```tsx
"use client"
import { useRef } from "react"
import gsap from "gsap"
import { ScrollTrigger } from "gsap/ScrollTrigger"
import { SplitText } from "gsap/SplitText"
import { useGSAP } from "@gsap/react"

gsap.registerPlugin(useGSAP, ScrollTrigger, SplitText)

export function Hero() {
  const scope = useRef<HTMLElement>(null)
  useGSAP(() => {
    const split = SplitText.create(".hero-title", { type: "lines", mask: "lines" })
    gsap.from(split.lines, { yPercent: 100, duration: 0.8, ease: "power3.out", stagger: 0.08 })
  }, { scope })   // selectors are scoped to this component; everything reverts on unmount
  return <section ref={scope}><h1 className="hero-title">…</h1></section>
}
```

- **Always `useGSAP`**, not raw `useEffect`: it scopes selectors and reverts tweens, ScrollTriggers and SplitText on unmount (and handles Strict Mode's double run).
- Animations started later (click handlers, timeouts) must be wrapped in `contextSafe()` so they're cleaned up too.
- `"use client"` on every file that uses GSAP; register plugins once.
- Pass `dependencies` (and `revertOnUpdate: true` if the animation should rebuild) when props change.

## Rules

- **Reduced motion:** wrap effects in `gsap.matchMedia()` with `(prefers-reduced-motion: no-preference)`; the reduced branch shows the final state.
- **Don't hide LCP content:** for heroes, prefer `gsap.from` with `immediateRender`, or set initial styles in CSS plus `autoAlpha`, so text doesn't flash or stay hidden without JavaScript. Keep the hero readable if the script fails.
- **ScrollTrigger:** call `ScrollTrigger.refresh()` after images or fonts change the layout; use `markers: true` only while developing; prefer `scrub` for narrative sections and pin sparingly (pinned sections are hard on mobile).
- **Responsive:** build breakpoint-specific timelines with `gsap.matchMedia()`, and test on a real phone.
- Animate transforms and opacity (`x`, `y`, `scale`, `autoAlpha`), not layout properties.
- **Smooth scrolling** (ScrollSmoother) breaks native scroll expectations: use it only on showcase sites, never on apps or long-form content.
- Timing: let `dean-design-taste` set the personality. Editorial sites get slow, calm eases (`power2/3.out`, 0.6–1.2s); avoid bouncy eases on serious brands.
