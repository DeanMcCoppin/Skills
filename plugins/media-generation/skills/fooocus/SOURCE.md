# Source

- Tool: https://github.com/lllyasviel/Fooocus
- Author: lllyasviel (Lvmin Zhang) and contributors
- License: GPL-3.0 (app); SDXL weights under CreativeML Open RAIL++-M
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at ae05379 (LICENSE, README status and features).

## Notes

- Verdict: good free offline Midjourney-style generator, but frozen on SDXL (LTS, bug fixes only). Fine for quick images; use Forge/ComfyUI or cloud models for state-of-the-art.
- Good at:
  - near-zero tuning
  - Midjourney-like features (vary, upscale, inpaint/outpaint, image prompt, styles)
  - runs on a 4GB NVIDIA GPU
  - offline and private
- Weak at / risks:
  - no newer model architectures (Flux and later)
  - slow on Mac/CPU
  - multi-GB downloads
  - fake Fooocus sites exist (official GitHub only)
  - the promo's "free vs $10/month" ignores hardware cost and the quality gap with current Midjourney
- Alternatives: Midjourney (paid, best aesthetics); WebUI Forge or ComfyUI (local, newer models); open-higgsfield (paid cloud models)
