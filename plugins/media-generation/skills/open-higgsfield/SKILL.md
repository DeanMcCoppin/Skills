---
name: open-higgsfield
description: "Set up and use Open Higgsfield, a self-hosted studio for AI image and video generation (Kling, Seedance, Wan, Flux, Higgsfield Soul and ~30 more models). Use when Dean wants lifelike or cinematic AI video, realistic AI photos, b-roll, product or hero shots generated for a site, or asks to \"use Higgsfield\", \"generate a video\" or \"run Open Higgsfield\"."
metadata:
  pricing: pay-per-use
  cost: "App free (self-host); every generation billed to your Higgsfield API key."
  tags: [ai-video, ai-image, higgsfield, kling, seedance]
---

# Open Higgsfield

[wide-trace/open-higgsfield](https://github.com/wide-trace/open-higgsfield) is a Next.js studio: one prompt bar, 38 image and video models, per-model settings, start/end-frame and reference inputs, and a gallery stored in the browser. It doesn't run any models itself. Every generation goes to a paid platform API using Dean's key.

## Before anything else

- **Cost.** Generations are billed by the generation platform (most likely Higgsfield's API credits), **not** by Dean's Claude subscription. Mention this before the first run, and estimate cost when batching or using 4K or long durations.
- **No license.** The repo has no LICENSE, so it's all rights reserved. Run it for Dean's own use only. Never copy its code into Dean's projects or this repo.
- **Keys stay local.** Never use the hosted site (openhiggsfield.ai): whoever hosts it controls where the key goes. Run it locally. Never commit keys, never paste them in chat logs or files in a repo, and never print them.

## Open Higgsfield or official Higgsfield?

Same models, same output: this is only a different front end and billing route.
- **Open Higgsfield**: occasional use, comparing many models, pay-as-you-go, scripting.
- **Official app + subscription**: heavy regular use (bundled credits are likely cheaper) or when Dean needs its presets, effects or character tools.
If Dean is unsure, ask roughly how many clips a month Dean expects, and point to the pricing page to compare. Full notes are in [SOURCE.md](SOURCE.md).

## Set up (once per machine)

1. Clone outside any project, pinned to the reviewed commit:
   ```bash
   git clone https://github.com/wide-trace/open-higgsfield ~/tools/open-higgsfield
   cd ~/tools/open-higgsfield && git checkout b16a0ef
   ```
   If Dean wants a newer version, first read the diff since `b16a0ef` (`git log -p b16a0ef..origin/main`) for new network calls, telemetry or changes to how the key is handled. Then update the pinned commit in this file.
2. `pnpm install` (needs Node 20+ and pnpm).
3. Create `.env.local`:
   ```
   HF_API_BASE_URL=<generation API base URL from the platform's official docs>
   OPEN_HIGGSFIELD_READ_WRITE_TOKEN=<Vercel Blob read-write token, only needed for image/video inputs>
   ```
   Get the base URL from the platform's own API docs (for Higgsfield: their developer/API page), not from forums or the hosted site. Without a Blob token, text-to-image and text-to-video still work; only uploads (start frames, references) fail.
4. `pnpm dev`, then open http://localhost:3000. Dean pastes the platform key (`id:secret`) into **Add key**; Claude never handles it. It's stored in an httpOnly cookie.

If anything about the API is unclear (base URL, key format, pricing), ask Dean or check the official docs. Don't guess.

## Using it for lifelike video

Claude's job is to write prompts, pick models and settings, and organize outputs. Dean presses generate.

- **Pick the model by the shot:**
  - photoreal people and faces: Higgsfield Soul (image), then Kling or Seedance image-to-video
  - camera-driven cinematic motion: Higgsfield DoP, Kling Pro or Master tiers
  - fast and cheap drafts: "Fast", "Turbo" or "Mini" variants
  - edits and extensions of an existing clip: Seedance Edit/Extend

  Model names change often, so check the in-app picker for what's current.
- **Image first, then animate.** For realism and consistency, generate a still you like and use it as the **start frame** (and optionally the end frame) for image-to-video. Reuse the same reference images across shots to keep the character and grade consistent.
- **Prompt structure** (one shot per prompt): subject and action → setting → camera (lens, framing, movement: "35mm, slow dolly-in, eye level") → light ("overcast window light", "golden hour backlight") → film look ("shot on Alexa, natural skin texture, subtle grain") → duration and pacing. Use plain physical description; avoid "ultra realistic 8K masterpiece" filler.
- **Realism killers to avoid:** too many subjects, fast complex motion, hands doing fine tasks, readable text or logos, extreme slow motion. Keep shots 4–6s and cut between them.
- **Draft cheap, finish expensive:** iterate on Fast/Turbo tiers at low resolution, then re-render the winner (**Reuse** restores the prompt and settings) on Pro/4K.
- **For websites:** match the site's aspect ratio (16:9 hero, 9:16 mobile, 4:5 cards). Export and compress (H.264/H.265 MP4 + WebM, poster frame, muted autoplay loop under ~5 MB), and store files in the project's assets, not as links to the platform's CDN, because those URLs expire.

## Don't

- Don't generate real, identifiable people without their consent, or anything deceptive (fake news footage, impersonation).
- Don't call the platform API directly with Dean's key from scripts unless Dean asks. Use the studio.
