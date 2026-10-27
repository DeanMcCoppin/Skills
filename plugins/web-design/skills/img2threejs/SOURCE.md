# Source

- Tool: https://github.com/img2threejs/img2threejs (Hoai Nho and contributors; Apache-2.0). `github.com/hoainho/img2threejs` serves the same commit (moved repo).
- This skill: Dean (original), written with Claude. Not vendored: the skill is ~470-line router plus `grimoire/`, `docs/`, `forge/` scripts, and changes daily. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit 3e7099e (skill v2.0.0, npm installer 0.1.1): README, SKILL.md header and rules, docs/INSTALL.md, `bin/img2threejs.mjs`, network/key grep of all Python and JS. Network in maintainer tooling only (`scripts/issue_triage.py`, CI) and the optional vision integration (downloads MediaPipe models from storage.googleapis.com). No telemetry or API keys. Not a full audit of `forge/`.
- Flags raised:
  - The README's install is `npx --yes img2threejs@latest install`: auto-confirmed, unpinned, and it symlinks into global skill folders of every detected agent. The skill uses a pinned project clone instead.
  - The optional `img2` harness installs plugins from a live catalog into `~/.img2` (third-party code, unreviewed).

## Notes

- Verdict: clever and genuinely useful for stylized 3D hero objects in code; niche for Dean's work. Try it on one product shot before promising it to a client.
- Good at: editable, animatable code output, a detail inventory, browser-rendered self-checks, resumable state.
- Weak at / risks: heavy usage (many vision passes), procedural limits (no photoreal), fast churn, a big codebase, likeness features for real people.
- Alternatives: `spline` (designed 3D scenes, easiest embed), a 3D artist or image-to-mesh services for GLB, R3F + drei primitives by hand.
