# Source

- Tools:
  - claude-code-setup, Anthropic (author Isabella He): https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-code-setup (Apache-2.0). Reviewed 2026-10-27 at commit 41f619d: README, plugin.json, `claude-automation-recommender/SKILL.md` (read-only by its own rules; tools Read, Glob, Grep, Bash), reference file list.
  - Skills CLI, Vercel: https://github.com/vercel-labs/skills (MIT; npm `skills`). Reviewed 2026-10-27 at commit 533c7df (v1.7.4): README, `skills/find-skills/SKILL.md`, telemetry section of docs/troubleshooting.md.
- This skill: Dean (original), written with Claude. Neither tool's skill vendored. License: TODO (this repo has no LICENSE file yet).
- Flags raised:
  - Vercel's `find-skills` skill instructs agents to run `npx skills add <owner/repo@skill> -g -y` ("installs globally… skips confirmation prompts"). That bypasses review, so it wasn't imported; this skill forbids it.
  - Skills CLI telemetry is on by default (anonymous; repo and skill IDs for public GitHub sources; security-audit requests). Opt-out `DISABLE_TELEMETRY=1` / `DO_NOT_TRACK=1`.
  - claude-code-setup: none. A Medium post claimed it installed automations; its SKILL.md says it doesn't create or modify files.

## Notes

- Verdict: claude-code-setup is a good once-per-project checklist (official, read-only). The skills CLI is the best search over the open skills ecosystem; use it to find, then import through add-skill.
- Weak at: the recommender also web-searches and can suggest popular but unreviewed tools; skills.sh ranks by installs, not quality or safety.
- Replaces the "Where to find more" notes in README as the place Claude reads this from.
