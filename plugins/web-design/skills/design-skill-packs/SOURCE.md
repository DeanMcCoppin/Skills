# Source

- Tools:
  - https://github.com/Leonxlnx/taste-skill (Leonxlnx; MIT), added 2026-10-27
  - https://github.com/pbakaus/impeccable (Paul Bakaus; Apache-2.0)
  - Frontend Design plugin, Anthropic (in the official `claude-plugins-official` marketplace; the claude-code repo is "All rights reserved", so nothing copied)
  - https://github.com/nextlevelbuilder/ui-ux-pro-max-skill (MIT)
  - https://github.com/kylezantos/design-motion-principles (Kyle Zantos; MIT)
- This skill: Dean (original hub), written with Claude. Nothing vendored: each pack installs from its official source. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27. Impeccable at d34c87e (README install and hooks sections), UI/UX Pro Max at 28b3b8d (README, plugin manifests, script network grep), design-motion-principles at 4a9ca87 (README, file list). Frontend Design from its public description only.
- taste-skill reviewed 2026-10-27 at commit 12af471 (v2.1.5): the full SKILL.md (542 lines), install.sh, plugin manifest, and every script grepped for network, exec and file writes. Network only in `assets.mjs` (open-collection image APIs, on demand, no keys); `inspect.mjs`/`scenes.mjs` serve files on 127.0.0.1 and launch a local Chrome over CDP; `draw.mjs` writes `~/.taste-skill/history.json`. No telemetry. `install.sh` symlinks into global `~/.claude/skills` (not used). Minor: "If the request is vague, decide and state your reading in one line instead of asking" conflicts with `karpathy-guidelines`.
- Flag raised: Impeccable downloads a self-contained engine binary on first run into `~/.impeccable/bin/` and its installer detects and can write global harness folders and hook manifests. The skill mandates `--scope=project` and pinning. It also installs an edit hook (default yes) and has opt-out telemetry to impeccable.style (roll API always called for new designs; choice recording opt-out). Documented, no code sent.

## Notes

- Verdict: Dean's own design skills already cover direction, motion and polish. Of the packs, Impeccable's deterministic detector is the most useful addition (rules-based slop checks); UI/UX Pro Max is a decent palette and font lookup; design-motion-principles is good for client-facing motion audit reports; Frontend Design is mostly redundant with dean-design-taste.
- taste-skill: the best pack for public pages. Good at: forcing a real direction instead of the average template, subject-specific ideas, real pictures with credits, browser-measured rules at three widths, separate app-screen rules, evals. Weak at: long and opinionated (a full house style that competes with dean-design-taste), heavy per run (scripts, screenshots, loops), older v1 variants (gpt-taste, brutalist etc.) still float around skill directories; use v2 from the repo. Star counts in third-party listings vary wildly (15k to 90k).
- Rule: one pack per project; Dean's skills override.
- Impeccable: good at concrete commands, a detector usable in CI or a browser, active development. Weak at: big monorepo, binary download, a hook-writing installer.
- UI/UX Pro Max: good at breadth of presets. Weak at: generic presets can pull toward template looks; lots of marketing in the README.
- design-motion-principles: good at structured audits and references. Weak at: overlaps the `motion` skill for build work.
- Alternatives: `design-system` (AI-slop audit), `refero` (real-world references), `interface-polish`.
