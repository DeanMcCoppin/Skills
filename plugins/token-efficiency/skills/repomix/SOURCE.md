# Source

- Tool: https://github.com/yamadashy/repomix (Kazuki Yamada and contributors; MIT)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit a835271 (README, CLI options, security check docs).
- No flags. The promo's `npx repomix@latest` is unpinned; the skill pins.

## Notes

- Verdict: a great utility for moving a codebase into tools without repo access, and for token counting. Not a way to save tokens inside Claude Code itself (there, search plus `graphify` is cheaper).
- Good at: one-command packs, `--compress`, remote repos, Secretlint on by default, MCP server mode, a web version.
- Weak at: big packs flood context; output can still include sensitive non-secret data (customer names, internal URLs).
- Alternatives: `graphify` (query a graph instead of dumping), gitingest, Claude Code reading the repo directly.
