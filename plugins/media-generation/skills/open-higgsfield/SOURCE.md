# Source

- Tool: https://github.com/wide-trace/open-higgsfield (author: wide-trace)
- Reviewed commit: b16a0ef (2026-09-17). Read-only review on 2026-10-27: the key is sent as `Authorization: Key id:secret` only to `HF_API_BASE_URL`; a search of `src/` found no other hard-coded hosts besides Vercel Blob uploads, and no telemetry. Not a full audit.
- Tool license: **none**. This skill only links to the tool and describes how to use it; no code from it is included here.
- Skill text: Dean (original), written with Claude. License: TODO (this repo has no LICENSE file yet).
- Notes: about 4.8k stars against 3 commits at review time. Re-review before updating the pinned commit.

## Notes

- Verdict: use it for pay-as-you-go generation and to try many models from one prompt bar. For heavy weekly use, the official Higgsfield subscription is probably cheaper and has more tools.
- What it really is: a free, self-hosted front end for Higgsfield's paid platform API. It runs no models itself, so output quality is identical to Higgsfield's.
- Cost: not covered by a Claude subscription. Every generation is billed to the platform key (`id:secret`). Subscription plans usually bundle credits at a discount, so per-generation API pricing can cost more at volume. Prices weren't verified; compare them on Higgsfield's pricing page.
- Good at:
  - no subscription
  - one composer and gallery across 38 models (8 image, 30 video)
  - batches of up to 4
  - Reuse/Recreate restores model, settings and prompt
  - start/end frames and references
  - hackable and scriptable
- Weak at / risks:
  - likely missing the official app's presets, effects and character tools
  - history only in the browser (IndexedDB, 60 records), and platform CDN URLs expire
  - unofficial: can break when the API changes, and there's no support
  - no license, so it can't be reused in projects
  - unknown author and an unusual stars-to-commits ratio
  - the hosted site (openhiggsfield.ai) would hold your key, so self-host only
- Alternatives: official Higgsfield web app (subscription); calling the platform API directly; other multi-model studios or APIs if Higgsfield's own models (Soul, DoP) aren't needed.
- Review: commit b16a0ef. Re-check network calls and key handling before moving the pin.
