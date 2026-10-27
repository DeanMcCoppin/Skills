# Source

- Source: https://github.com/oso95/scroll-world (skill folder `skills/scroll-world`)
- Author: cyw (oso95)
- License: MIT
- Imported: 2026-10-27 at commit 71cc36d (plugin version 0.8.0). Every file was read in full (SKILL.md, prompts.md, pipeline.md, scrub-engine.js, index-template.html, knockout.py, README, manifests); nothing was executed.
- Changes:
  - removed `allowed-tools: Bash, Read, Write, Edit, AskUserQuestion, Skill`, so paid generation commands go through normal permission prompts
  - added a cost-approval note at the top
  - description rewritten for triggering
  - split Gotchas, the model/backend details and the budget details into references/gotchas.md, models.md and budget.md, to keep SKILL.md near 500 lines
  - replaced the macOS-only `stat -f%z` in pipeline.md with portable `wc -c`
  - replaced a reference to a `higgsfield-generate` skill that isn't in this repo
  - the scrub engine, template, knockout script and prompts are unchanged

## Notes

- Verdict: a genuinely impressive, well-engineered pipeline for Apple-style scroll cinematics. Use it for flagship client landing pages where the budget allows (~$11–30 per desktop chain, about double with mobile), not for everyday sites.
- Review findings:
  - No phoning home: the scrub engine only fetches the page's own clip files, and copy is HTML-escaped.
  - No download-and-execute and no rule overrides.
  - Credentials stay with the official CLIs: Dean runs `higgsfield auth login`; Claude never handles the login.
  - Data flow to know about: prompts and frames go to the paid providers (Higgsfield, Monid's Seedance, optionally Codex image_gen). Monid's `sfs` uploads frames as **public signed URLs** (1 hour to 1 day TTL), so don't use confidential imagery.
  - The optional Codex step runs `codex exec -s workspace-write` (another agent with write access to the scratch dir).
- Good at:
  - frame-identical seams (real-frame handoff plus crossfade)
  - two camera architectures with honest trade-offs
  - asks before every costly choice (camera, mobile, budget)
  - a portable zero-dependency scrub engine (blob seeking, lazy load, reduced motion, iOS and mobile hardening)
  - detailed QA and gotchas
- Weak at / risks:
  - depends on fast-moving third-party APIs and CLIs (Monid's catalog changes; re-inspect each build)
  - generation takes hours of background jobs
  - NSFW false positives on interiors
  - heavy video assets (watch LCP and mobile data)
  - scroll-jacking feel: always keep the copy and CTA readable and the page navigable
  - Monid is a lesser-known service
- Alternatives:
  - `gsap` ScrollTrigger with stills and parallax (no generation cost)
  - `spline` (real-time 3D instead of pre-rendered video)
  - `remotion` (code-made video)
  - `open-higgsfield` for manual clip generation
- Overlap: complements `open-higgsfield` (manual studio) and `gsap` (code-driven scroll); no duplicate.
