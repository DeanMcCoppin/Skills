---
name: spline
description: Design interactive 3D scenes in Spline and embed them in websites (React/Next.js via @splinetool/react-spline, or iframe/viewer) - hero objects users can drag and rotate, 3D product showcases, playful interactive backgrounds - with performance, mobile and accessibility fallbacks. Use when Dean wants real 3D on a site, an interactive 3D hero, a draggable object, or mentions Spline.
---

# Spline

[Spline](https://spline.design) is a browser-based 3D design tool. You design and animate a scene (objects, materials, lights, states, events such as hover, click and drag), then export it to run on the web.

## Plan: check first

- **Free:** web export works but **shows the Spline logo**, with limited personal files.
- **Hobby (~$12/month yearly):** removes the watermark from 3D web exports, and adds AI 3D/texture generation.
- **Pro (~$25/month yearly):** code export download and more.
- For client sites, budget at least Hobby so there's no watermark. Prices are as of 2026-10-27; check spline.design/pricing.

## Embed in Next.js

```bash
npm i @splinetool/react-spline @splinetool/runtime
```

```tsx
// Server-friendly: renders a placeholder while the scene loads
import Spline from "@splinetool/react-spline/next"

export function Hero3D() {
  return <Spline scene="https://prod.spline.design/<id>/scene.splinecode" />
}
```

- In client components, use `@splinetool/react-spline` with `onLoad={(app) => …}` to access the scene, for example `app.findObjectByName("Cube")` or `app.emitEvent("mouseHover", "Button")` to tie it to site interactions.
- Reserve the space (fixed aspect ratio box) so loading doesn't shift the layout.
- Load it **below the fold or after first paint** where possible, and never let the 3D block the headline or CTA.

## Performance and fallbacks

- Keep scenes light: low-poly geometry, few lights, baked or simple materials, small textures, and the smallest export quality that looks right. Test the scene size before shipping.
- **Mobile:** serve a static image or short video on small or low-power devices (or `prefers-reduced-motion`), and only load the runtime on capable screens. Touch dragging can also hijack page scroll, so limit drag regions on mobile.
- **Accessibility:** the 3D is decorative unless it carries meaning. Give the container `aria-hidden` or a text alternative, make sure page content and CTAs don't depend on it, and keep keyboard users unblocked.
- Respect `dean-design-taste`: colors and materials should match the site palette, with one strong 3D moment per page. Avoid default glossy blobs and generic gradients.

## Alternatives

- **React Three Fiber (`@react-three/fiber` + drei):** full code control, smaller and more custom, but more work. Use it when the 3D needs app logic or data.
- **Bencho** has light pseudo-3D blocks (tilt, ASCII cube) when real 3D is overkill.
