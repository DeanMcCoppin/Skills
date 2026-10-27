---
name: dean-design-taste
description: "Dean's default design and frontend stack. Use whenever building or restyling any web UI (pages, components, landing pages, dashboards, maps), choosing fonts, colors, layout or animation, or starting a new frontend project. Apply these defaults unless the project already has its own design system."
metadata:
  pricing: free
  cost: "Free: house style."
  tags: [design, nextjs, tailwind, house-style]
---

# Dean's design taste

Defaults for every UI you build for me. If the project already has a design system or brand guide, follow that instead and use this only to fill gaps.

## Stack

- Next.js (App Router) + React + TypeScript (strict). No plain JS.
- Tailwind CSS for styling. Put design tokens (colors, fonts, radii, shadows) in the Tailwind theme / CSS variables, not as one-off arbitrary values.
- Framer Motion (`motion/react`) for animation. Rules and patterns are in the `motion` skill.
- Maps: Mapbox GL JS (preferred) or Google Maps JS API. Load keys from env vars, never hard-code them.

## Before building: set a direction

Answer these in a few lines before writing UI code:
1. **Purpose:** what job does this screen do?
2. **Audience:** who uses it, how often, and what do they scan first?
3. **Tone:** utilitarian, editorial, playful, technical, calm, dense, maximal… pick one on purpose. Tools for daily use should be quiet and scannable; launch pages and portfolios can be expressive.
4. **Memorable detail:** the one idea that makes it feel intentional.
5. **Constraints:** existing components and tokens, accessibility, performance, target viewports.

Use the project's existing components, tokens and icons before introducing anything new. The first screen should show the real product, tool or object, not marketing filler in front of it.

## Look and feel

- Modern and distinctive. It should look designed for this product, not generated.
- Avoid the generic AI look: no default purple/indigo-to-pink gradients, no glassmorphism by default, no centered-hero-plus-three-feature-cards template, no emoji as icons.
- Pick one clear visual idea per project (a strong typographic system, an unusual grid, a bold accent color) and commit to it.
- Strong type hierarchy: large confident headings, comfortable body line length (60–75ch), generous whitespace.
- Restrained palette: neutrals plus one or two accents. Check contrast meets WCAG AA.
- Design light and dark mode together.
- Real-looking content, not lorem ipsum. Use real or generated assets when the UI depends on images, products, places or people.
- No cards inside cards, no decorative blobs, no vague hero copy, and no new dependency just for a flourish.
- Long labels must wrap or resize cleanly on mobile and desktop. Grids, toolbars and counters keep stable dimensions when content or hover states change.

## Content states

Design every state that applies, each with clear feedback and a safe next action:

| State | Needs |
| --- | --- |
| Loading | stable layout (skeleton), progress, cancel where possible |
| Empty | why it's empty, plus a useful next action |
| Error | the specific failure, plus a recovery path |
| Partial | the available data, with missing parts clearly marked |
| Success | confirmation, plus the next step or undo |
| Permission | what's restricted and how to request access |

If a state doesn't apply, say why. "Couldn't test it" means untested, not "not applicable".

## Motion

- Every animation needs a purpose: show hierarchy, give feedback, or explain a state change. No decoration for its own sake.
- Prefer subtle, fast transitions (150–400ms) with spring or ease-out curves. Stagger lists lightly.
- Animate `transform` and `opacity`; avoid animating layout-heavy properties.
- Respect `prefers-reduced-motion` (`useReducedMotion`), and fall back to instant or fade-only.

## Finish gate (before calling UI done)

Check the **rendered** UI, not just the source, at the target viewports (at least about 390px wide and 1440px wide):
- keyboard navigation, visible focus, labels, contrast, touch targets, reduced motion
- narrow and wide layouts with long content
- each applicable content state

Save screenshots if a browser tool is available, and report anything untested instead of claiming it passed. For the detailed polish and a11y passes, see `interface-polish` and `accessibility` (code-audit).

## Maps

- Custom map style that matches the site palette, never the default style unchanged.
- Smooth `flyTo`/`easeTo` camera moves, clustered markers at density, custom marker components, and popups/drawers that match the rest of the UI.
- Lazy-load the map library and show a skeleton while it loads. Handle a missing/invalid token gracefully.

## TODO (Dean to fill in)

- TODO: Primary font (headings): ___
- TODO: Body font: ___
- TODO: Mono font: ___
- TODO: Brand / accent colors (hex): ___
- TODO: Neutral scale preference (warm / cool / pure gray): ___
- TODO: Default border radius and shadow style: ___
- TODO: Preferred component libraries (e.g. shadcn/ui, Radix, Aceternity, Magic UI): ___
- TODO: Default Mapbox style URL: ___
- TODO: Sites whose design I like (references): ___
