---
name: dean-design-taste
description: Dean's default design and frontend stack. Use whenever building or restyling any web UI (pages, components, landing pages, dashboards, maps), choosing fonts, colors, layout or animation, or starting a new frontend project. Apply these defaults unless the project already has its own design system.
---

# Dean's design taste

Defaults for every UI you build for me. If the project already has a design system or brand guide, follow that instead and use this only to fill gaps.

## Stack

- Next.js (App Router) + React + TypeScript (strict). No plain JS.
- Tailwind CSS for styling. Put design tokens (colors, fonts, radii, shadows) in the Tailwind theme / CSS variables, not as one-off arbitrary values.
- Framer Motion (`motion`) for animation.
- Maps: Mapbox GL JS (preferred) or Google Maps JS API. Load keys from env vars, never hard-code them.

## Look and feel

- Modern and distinctive. It should look designed for this product, not generated.
- Avoid the generic AI look: no default purple/indigo-to-pink gradients, no glassmorphism by default, no centered-hero-plus-three-feature-cards template, no emoji as icons.
- Pick one clear visual idea per project (a strong typographic system, an unusual grid, a bold accent color) and commit to it.
- Strong type hierarchy: large confident headings, comfortable body line length (60–75ch), generous whitespace.
- Restrained palette: neutrals plus one or two accents. Check contrast meets WCAG AA.
- Design light and dark mode together.
- Real-looking content and states (empty, loading, error), not lorem ipsum.

## Motion

- Every animation needs a purpose: show hierarchy, give feedback, or explain a state change. No decoration for its own sake.
- Prefer subtle, fast transitions (150–400ms) with spring or ease-out curves. Stagger lists lightly.
- Animate `transform` and `opacity`; avoid animating layout-heavy properties.
- Respect `prefers-reduced-motion` (`useReducedMotion`), and fall back to instant or fade-only.

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
