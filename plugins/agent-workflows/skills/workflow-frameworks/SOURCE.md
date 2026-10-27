# Source

- Tools: https://github.com/mattpocock/skills (Matt Pocock, MIT; added 2026-10-27), https://github.com/addyosmani/agent-skills (Addy Osmani, MIT; added 2026-10-27), https://github.com/obra/superpowers (Jesse Vincent / Prime Radiant, MIT) and https://github.com/open-gsd/gsd-core (Open GSD, MIT; formerly https://github.com/glittercowboy/get-shit-done, MIT, which now only points to gsd-core).
- This skill: Dean (original), written with Claude. Nothing vendored: install each from its official source so updates stay upstream. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27. Superpowers at 2ce8aa1 (README, hooks.json, session-start, using-superpowers, skill list, telemetry section). GSD Core at d909640 (README, install docs, hooks list, update-check worker); old repo at bdcaab2. Not a full audit of either.
- Matt Pocock's skills reviewed 2026-10-27 at commit 59db609: README (install, setup, rationale), marketplace/plugin manifests, file tree (no hooks), grill-me, git-guardrails-claude-code, grep of all SKILL.md files for URLs, global paths and installs. Clean; the only global-scope option (git-guardrails) asks first.
- Addy Osmani's agent-skills reviewed 2026-10-27 at commit aeac41d (v0.6.13): manifests (no hooks wired), hooks/session-start.sh (inert by default), sdd-cache hooks (curl HEAD to doc URLs, not wired), skill list. Clean.
- Flags raised:
  - Superpowers' `using-superpowers` is injected every session and phrased as an override ("<EXTREMELY-IMPORTANT> … YOU DO NOT HAVE A CHOICE. YOU MUST USE IT"). Not malicious, but it changes Claude's behavior everywhere it's enabled, so the skill says project scope only.
  - Superpowers telemetry: logo fetch with the version number (opt-out documented).
  - GSD: ~30 hooks and a background `npm view` update check at session start; the installer offers global scope. The skill mandates `--local` and a pinned version.

## Notes

- Matt Pocock's skills: the best default. Good at: alignment (`grill-me`), spec and ticket flows, TDD seams, bug diagnosis, no hooks. Weak at: tied to an issue-tracker workflow, many in-progress skills, ships via the official marketplace (updates automatically).
- Addy Osmani's agent-skills: good at a complete lifecycle checklist and reviewer agents (incl. web performance). Weak at: overlaps Dean's audit and design skills; generic in places.

- Verdict: both are good. Superpowers is the lighter, better default for feature work; GSD suits long greenfield builds that span many sessions. Never install both in one project.
- Superpowers is good at: TDD discipline, systematic debugging, worktree-based subagent execution, a review loop. Weak at: heavy ceremony for small tasks, an aggressive always-on meta skill.
- GSD is good at: durable state in `.planning/`, phase boundaries, context-rot protection, prompt-injection and secret-read guards. Weak at: weight (many hooks), fast churn, and the repo move (old installs and tutorials point to the old package).
- Everything Claude Code (affaan-m/everything-claude-code) is the same as ECC, which was already cherry-picked into this repo (strategic-compact, security-review, production-audit and others). Don't install it whole.
- Alternatives: Claude Code's plan mode plus `karpathy-guidelines` for small work; native subagents and agent teams.
