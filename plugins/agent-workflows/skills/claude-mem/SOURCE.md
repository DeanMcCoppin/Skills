# Source

- Tool: https://github.com/thedotmack/claude-mem (Alex Newman / thedotmack; Apache-2.0)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit 35f2ec0 (README, docs/public/installation.mdx, cmem-pro-headless.mdx, telemetry.mdx). The worker and hooks weren't audited line by line.
- Flags raised:
  - The interactive installer pre-selects hosted CMEM Pro (OAuth pairing at cmem.ai, then checkout), so compression runs on their servers unless `--provider claude` (local, Dean's Claude plan) is passed. Local installs still contact cmem.ai once at signup with a numbers-only usage summary.
  - PostHog telemetry is on by default (anonymous install UUID, whitelisted fields; documented). Opt out with `npx claude-mem telemetry disable` or `DO_NOT_TRACK=1`.
  - The skill mandates `--provider claude` and telemetry off.

## Notes

- Verdict: useful for long-running projects, but hosted-first install and opt-out telemetry make it a careful install. Local mode only; try `CLAUDE.md` plus a decisions file first.
- Good at: automatic capture (no discipline needed), semantic search over past sessions, `<private>` exclusions, a web viewer for the memory stream.
- Weak at / risks: hosted-by-default, a background worker and Bun dependency, extra Claude usage for compression, stale or wrong memories injected with confidence.
- Alternatives: CLAUDE.md and notes files (free, reviewable in git), `knowledge` plugin tools for document memory.
