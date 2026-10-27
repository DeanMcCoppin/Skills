---
name: img2threejs
description: "Rebuild an object or character from a single reference image as editable procedural Three.js code (a TypeScript THREE.Group factory plus a JSON spec, not a downloaded mesh) with img2threejs's staged blockout-to-lighting pipeline and screenshot-vs-reference self-correction - installed per project, pinned. Use when Dean wants a 3D product, prop or mascot on a site built in Three.js / React Three Fiber from a photo or sketch, an animatable 3D hero object without a 3D artist, or mentions img2threejs."
metadata:
  pricing: free
  cost: "Free (Apache-2.0). Uses Claude usage for many build-and-review passes; optional vision extras (SAM2, Depth Anything, MediaPipe) run locally but need large model downloads."
  tags: [3d, threejs, image-to-3d, procedural, webgl, hero]
---

# img2threejs

[img2threejs/img2threejs](https://github.com/img2threejs/img2threejs) (Apache-2.0; `hoainho/img2threejs` redirects to the same repo) is a large skill: it classifies the subject (object, character, hybrid), writes a sculpt spec with a detail inventory, then builds in passes (`blockout → structural → form → material → surface → lighting`), rendering each in a browser and comparing it with the reference. Output is code you can edit and animate.

## When it fits (and when Spline is better)

- ✅ A stylized product, prop, device or mascot for a hero, built from primitives and shaders, that you want as code in a Three.js/R3F project.
- ❌ Photoreal scans, complex organic models, or anything a client needs as GLB for other tools: use a 3D artist, a real image-to-mesh service, or `spline` for designed 3D scenes.
- Characters of **real people**: only with that person's consent, and never for client work that implies endorsement.

## Install (project-scoped, pinned)

```bash
git clone https://github.com/img2threejs/img2threejs.git .claude/skills/img2threejs
git -C .claude/skills/img2threejs checkout <reviewed-commit>
```

- **Don't run `npx --yes img2threejs@latest install`.** It auto-confirms, runs the latest unreviewed version, and links the skill into every agent's **global** folder it finds (`~/.claude/skills`, `~/.codex/skills`…).
- Skip the optional `img2` plugin harness (`~/.img2`, a live plugin catalog) unless Dean needs a domain profile; each plugin is new third-party code to review.
- Needs Python 3.10+ and a browser for previews (`playwright-cli` works). Add `.claude/skills/img2threejs` to `.gitignore` or commit it deliberately.

## Use

Attach the reference image and ask: `/img2threejs` rebuild this as a Three.js model for the hero. Then:
- put the generated group into the scene with Dean's lighting and camera; keep the polygon and draw-call budget mobile-friendly
- respect `prefers-reduced-motion` for any animation, and give a static image fallback on low-end devices (same rule as `spline`)
- expect many passes: set a stop point (for example "stop after the material pass") to control usage
