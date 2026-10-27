---
name: remotion
description: Make videos with code using Remotion (React): product demos, launch and promo videos, animated explainers, social clips, data-driven or templated videos, captions and charts. Use when Dean wants to create or edit a video programmatically in React, render MP4s from components, build a video template, or works in a Remotion project.
---

# Remotion

[Remotion](https://www.remotion.dev) renders React components to video: each frame is a render of your components at a given `useCurrentFrame()`.

## License: check first

Remotion isn't MIT. It's free for individuals and for companies of up to 3 people; larger companies need a paid company license. Check remotion.dev/license before using it in client or agency work, and note which applies in the project README.

## Use the official skills for the details

Remotion maintains its own agent skills, which stay current with its fast-moving API: [remotion-dev/skills](https://github.com/remotion-dev/skills). Install them in the Remotion project (that repo has no LICENSE file, so it isn't vendored here; read it before installing):

```bash
npx skills add remotion-dev/skills
```

They cover compositions, sequencing, timing and springs, transitions, audio, captions, fonts, images, videos, GIFs, Lottie, 3D, charts, Tailwind, and measuring text and DOM nodes.

## Defaults for Dean

- Start a project with `npx create-video@latest` (pick the TypeScript + Tailwind template). Preview in Remotion Studio (`npx remotion studio`) and render with `npx remotion render`.
- Drive everything from frames: `useCurrentFrame()`, `interpolate()` with `extrapolateRight: "clamp"`, and `spring()`. **Never CSS transitions or Framer Motion** inside compositions, because they don't render deterministically.
- Use `<Sequence>` / `<Series>` for timing, and `calculateMetadata` for durations that depend on data or media length.
- Use the project's brand tokens and fonts (load fonts with `@remotion/google-fonts` or `staticFile`) so videos match the site (`dean-design-taste`, `editorial-themes`).
- Export: H.264 MP4 for the web (plus WebM if needed), a poster frame, and captions. For site heroes, keep loops short and muted, and compress.
- Pair with `voicestudio` for voiceover, `open-higgsfield` for generated footage, and `cap` for screen captures to edit in.
