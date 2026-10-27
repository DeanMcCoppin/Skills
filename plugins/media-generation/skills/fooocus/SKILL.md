---
name: fooocus
description: "Generate images locally and offline with Fooocus, a free Midjourney-style app on Stable Diffusion XL (text-to-image, upscale, variations, inpaint/outpaint, image prompts, styles), on a 4GB+ NVIDIA GPU or Apple Silicon. Use when Dean wants free, private, offline image generation (hero art, mood images, placeholders, textures), compares Midjourney, or mentions Fooocus or SDXL."
metadata:
  pricing: free
  cost: "Free (GPL-3.0), runs locally; needs an NVIDIA GPU with 4GB+ VRAM (or a slow Mac/CPU path). SDXL model weights are free under the Open RAIL++-M license."
  tags: [ai-image, stable-diffusion, sdxl, local-ai, midjourney-alternative]
---

# Fooocus

[lllyasviel/Fooocus](https://github.com/lllyasviel/Fooocus) gives Midjourney-like results with almost no tuning, fully offline.

## Status: check first

- **Limited long-term support: bug fixes only.** It's built on **SDXL** and won't add newer architectures (Flux and later). The author recommends **WebUI Forge** or **ComfyUI** for newer models.
- Use Fooocus for quick, free, good-enough images. For top quality or the newest models, use Forge/ComfyUI locally, or paid cloud models via `open-higgsfield`.
- **Only download from the official GitHub repo.** The README warns that fake Fooocus websites rank on Google.

## Install

- **Windows:** download the official 7z from the repo's README "Download" section, extract it, and run `run.bat` (or `run_realistic.bat` / `run_anime.bat`). Models download on first run (several GB).
- **Linux/macOS:** clone, create a Python 3.10 venv, `pip install -r requirements_versions.txt`, then `python entry_with_update.py` (add `--preset realistic` for photos). Apple Silicon works but is slow. Follow the README's platform notes.
- Minimum about 4GB NVIDIA VRAM and 8GB+ RAM, with plenty of disk for models.

## Using it well

- Write prompts as plain descriptions; Fooocus expands them (the "Fooocus V2" style). Pick a style preset, then an aspect ratio matching the slot: 16:9 hero, 4:5 cards, 1:1 avatars.
- Use **Vary** and **Upscale** (2x) for finals; **Inpaint/Outpaint** to fix details or extend backgrounds; **Image Prompt** to keep a consistent look across a set.
- Keep a site cohesive with one style and palette words reused in every prompt (the same idea as `editorial-themes` / `scroll-world` style preambles).
- Export WebP/AVIF at the display size for the web. Don't ship raw 1024px PNGs.

## Don't

- Don't generate real, identifiable people or brand logos, or imitate living artists' signature styles for client work.
- The SDXL license (Open RAIL++-M) allows commercial use but forbids listed harmful uses. Keep generated images for legitimate content.
