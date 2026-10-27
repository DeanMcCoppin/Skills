# Source

- Tool: https://github.com/louislva/claude-peers-mcp
- Author: louislva
- License: MIT
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at 640183f (LICENSE, README; Getting Started v0.8.3 via search).
- Dean approved adding it with guardrails.

## Notes

- Verdict: a clever way for separate sessions to talk, but only with the guardrails. Native subagents or agent teams are the safer default.
- Good at:
  - simple local broker
  - list, send, broadcast and summaries
  - instant push via channels
  - federation option
- Weak at / risks:
  - **flagged at review:** the README's launch command adds `--dangerously-skip-permissions`; combined with channels, any process that can reach the broker can inject instructions that run unprompted (the skill forbids this)
  - channel push ~50–70% reliable (their docs)
  - needs claude.ai login and Bun
  - the development-channels flag is experimental
- Alternatives: Claude Code subagents and agent teams; a shared notes file; one session with `--add-dir`
