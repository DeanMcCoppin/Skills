# Source

- Tools:
  - https://github.com/pbakaus/impeccable (Paul Bakaus; Apache-2.0)
  - Frontend Design plugin, Anthropic (in the official `claude-plugins-official` marketplace; the claude-code repo is "All rights reserved", so nothing copied)
  - https://github.com/nextlevelbuilder/ui-ux-pro-max-skill (MIT)
  - https://github.com/kylezantos/design-motion-principles (Kyle Zantos; MIT)
- This skill: Dean (original hub), written with Claude. Nothing vendored: each pack installs from its official source. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27. Impeccable at d34c87e (README install and hooks sections), UI/UX Pro Max at 28b3b8d (README, plugin manifests, script network grep), design-motion-principles at 4a9ca87 (README, file list). Frontend Design from its public description only.
- Flag raised: Impeccable downloads a self-contained engine binary on first run into `~/.impeccable/bin/` and its installer detects and can write global harness folders and hook manifests. The skill mandates `--scope=project` and pinning. It also installs an edit hook (default yes) and has opt-out telemetry to impeccable.style (roll API always called for new designs; choice recording opt-out). Documented, no code sent.

## Notes

- Verdict: Dean's own design skills already cover direction, motion and polish. Of the packs, Impeccable's deterministic detector is the most useful addition (rules-based slop checks); UI/UX Pro Max is a decent palette and font lookup; design-motion-principles is good for client-facing motion audit reports; Frontend Design is mostly redundant with dean-design-taste.
- Rule: one pack per project; Dean's skills override.
- Impeccable: good at concrete commands, a detector usable in CI or a browser, active development. Weak at: big monorepo, binary download, a hook-writing installer.
- UI/UX Pro Max: good at breadth of presets. Weak at: generic presets can pull toward template looks; lots of marketing in the README.
- design-motion-principles: good at structured audits and references. Weak at: overlaps the `motion` skill for build work.
- Alternatives: `design-system` (AI-slop audit), `refero` (real-world references), `interface-polish`.
