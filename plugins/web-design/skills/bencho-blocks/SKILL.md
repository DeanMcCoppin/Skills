---
name: bencho-blocks
description: "Add polished interactive React micro-interactions from Bencho (bencho.dev): tilt cards, magnetic docks, swipe decks, slide-to-confirm, rolling counters, signature pads, liquid toggles, loaders, plus synthesised UI sounds. Use when Dean wants a component to feel delightful or tactile, asks for micro-interactions, hover/drag/press effects, a fancy toggle, counter, carousel, upload zone or OTP input, or mentions Bencho."
metadata:
  pricing: freemium
  cost: "44 free MIT blocks; Pro €79/yr or €99 once for 140+ more and the MCP."
  tags: [micro-interactions, react, framer-motion, ui-sounds]
---

# Bencho blocks

[Bencho](https://bencho.dev) is a library of interactive React blocks and Web Audio UI sounds by Lorenzo Cabra.
- **Free:** 44 blocks and 24 sounds in [cabralorenzo/bencho](https://github.com/cabralorenzo/bencho), MIT licensed.
- **Pro:** 140+ more blocks, the Bencho MCP, and downloads (€79/year, or €99 once for early members). Pro blocks are under the Bencho Pro licence: use them in any project, but never redistribute them as a kit or library, and never commit them to this skills repo.

## When to reach for one

Use a block where interaction **is** the point: a hero toy, a signature moment in a product (like/reaction, pay button, confirm), onboarding, playful empty states. Use at most one or two per page. Don't put them on every button. They must still respect `dean-design-taste` and `prefers-reduced-motion`.

## Add a free block

1. Browse the live demos on bencho.dev, or the list in the repo README (grouped by Hover, Swipe, Drag, Slide, Press, Type, Select). Tune the props on the site; the same values work as props in code.
2. Get the source, pinned to the reviewed commit:
   ```bash
   git clone https://github.com/cabralorenzo/bencho /tmp/bencho && git -C /tmp/bencho checkout 30ab35a
   ```
3. **Read the block's files before copying** (component, CSS, README): check its imports, and that it makes no network calls.
4. Copy it into the project: `cp -r /tmp/bencho/blocks/<block> src/components/<block>`. Install only the deps that block imports (`framer-motion`/`motion`, `lucide-react`, sometimes `three` or `liquid-gooey`).
5. **Fit it to the project:**
   - Blocks ship plain CSS that reads variables from `tokens.css`. Map those variable names to the project's Tailwind/CSS tokens instead of importing Bencho's palette wholesale.
   - Next.js App Router: add `"use client"` to the component, and lazy-load heavy ones (`three`) with `next/dynamic` and `ssr: false`.
   - Dark mode follows `data-theme="dark"` or the system setting. Make sure that matches how the project switches themes.
   - Add a reduced-motion fallback if the block lacks one. Check keyboard and screen-reader use for anything interactive, and add labels and roles where missing.
6. Keep the MIT notice: add a header comment `// Adapted from Bencho (MIT), https://github.com/cabralorenzo/bencho` to the copied component.

## Sounds

`sounds/sounds.ts` synthesises 24 UI sounds with the Web Audio API, with no audio files (`play("tick")`). Off by default: play only on direct user actions, keep them quiet, and give users a way to mute.

## Pro (only if Dean has a plan)

The Bencho MCP lets Claude Code find and add any block directly. Connect it with the steps on bencho.dev/mcp using Dean's own account. Never commit Pro block source to a public repo or to this skills repo.
