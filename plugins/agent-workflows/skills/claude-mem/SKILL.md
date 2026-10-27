---
name: claude-mem
description: "Give Claude Code persistent memory across sessions with claude-mem (captures tool observations, compresses them into a local SQLite + Chroma store, injects relevant context at session start, searchable via MCP) - set up local-only, because the interactive installer defaults to a hosted service and telemetry is on by default. Use when Dean wants Claude to remember past sessions or decisions in a project, keeps re-explaining context, asks about memory plugins, or mentions claude-mem."
metadata:
  pricing: freemium
  cost: "Local mode free (Apache-2.0); summarization uses Dean's Claude usage. The installer's default is the hosted CMEM Pro service with optional Cloud Sync to cmem.ai (paid tiers; check cmem.ai)."
  tags: [memory, context, sessions, mcp, sqlite, claude-code]
---

# claude-mem

[thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) (Apache-2.0) hooks into Claude Code's lifecycle, records what tools did, compresses it into observations with a local worker (Bun, SQLite plus Chroma vectors), and feeds relevant memories into new sessions. It adds MCP search tools for "what did we decide about X?".

## First: do you need it?

Cheaper, native options cover most cases:
- the project's `CLAUDE.md` for durable rules and decisions (Claude reads it every session)
- a `docs/decisions.md` or `NOTES.md` that Claude updates at the end of a task
- `strategic-compact` for long single sessions

Use claude-mem when a project runs over many sessions and those files keep falling behind.

## Install: local only

```bash
DO_NOT_TRACK=1 npx claude-mem@<pinned-version> install --provider claude
npx claude-mem telemetry disable
```

- **Interactive `npx claude-mem install` pre-selects hosted CMEM Pro** (OAuth pairing with cmem.ai, then a checkout or trial). Always pass `--provider claude`: memory is stored locally and compressed with Dean's own Claude plan. Local installs still ping cmem.ai once at signup with a numbers-only usage summary.
- **Telemetry (PostHog) is on by default.** Turn it off with `npx claude-mem telemetry disable`, or set `DO_NOT_TRACK=1` in the shell profile; answer "no" when the installer asks.
- Leave **Cloud Sync** off. Never sync client projects.
- Settings live in `~/.claude-mem/settings.json`; the database lives in `~/.claude-mem/`. Back it up or wipe it like any other data. Flag names change, so check the pinned version's installation docs.

## Privacy

- It records tool inputs and outputs, so file contents, commands and error messages land in the store. Wrap anything sensitive in `<private>…</private>` so it's skipped.
- Don't let it capture secrets: keep keys in `bitwarden` / env vars, not in files Claude reads.
- Memories are hints, not truth. If one contradicts the code or `CLAUDE.md`, the code and `CLAUDE.md` win; fix or delete the memory.
