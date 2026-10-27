---
name: headroom
description: "Compress what Claude Code reads (tool outputs, logs, JSON, search results, file dumps) through Headroom, a local open-source proxy/MCP that shrinks context reversibly (originals kept locally, retrievable) - set up per session with telemetry off and measured before trusting the savings. Use when Dean hits context or usage limits on log-, JSON- or search-heavy sessions, wants to cut API token costs for agents, or mentions Headroom or context compression."
metadata:
  pricing: free
  cost: "Free (Apache-2.0), runs locally. Headroom Enterprise (teams, routing, injection filtering) is paid."
  tags: [context, compression, tokens, proxy, mcp, costs]
---

# Headroom

[chopratejas/headroom](https://github.com/chopratejas/headroom) (Apache-2.0; PyPI `headroom-ai`) sits between the agent and the model and compresses tool outputs and other bulky context before the model reads them. Originals stay on disk; the model can call `headroom_retrieve` to get the full text back.

## First: is it worth it?

- Biggest wins are on **JSON, logs, CSV and search output** (vendor-reported 60–95%). On normal coding sessions independent reviews report ~15–20%.
- Try the free, native levers first: `strategic-compact`, `graphify` for code questions, `repomix --compress` for snapshots, limiting test and log output in commands.
- On a Claude subscription, savings mean longer before limits; on the API, lower bills.

## Setup (pinned, telemetry off)

```bash
uv tool install --python 3.13 "headroom-ai[all]==<pinned-version>"
export HEADROOM_TELEMETRY=off            # anonymous beacon is ON by default; or DO_NOT_TRACK=1
headroom wrap claude --code-memory none  # one wrapped session; skips installing Serena
headroom doctor && headroom dashboard    # confirm routing, watch real savings
headroom unwrap claude                   # undo
```

- `headroom wrap` starts a local proxy and routes Claude Code through it (`ANTHROPIC_BASE_URL`). **All of Dean's prompts, code and tool output pass through it**, on Dean's machine. Keep it bound to localhost and pinned to a reviewed version.
- By default `wrap` also installs the **Serena** MCP server (`~/.claude.json`, local scope). Use `--code-memory none` unless Dean wants it.
- It downloads ML models (Hugging Face) on first use. Never set `HEADROOM_TLS_STRICT=0` casually.
- `headroom learn` writes "corrections" into `CLAUDE.local.md` (or `CLAUDE.md` with `--target`): review every line before keeping it.

## While it's on

- Lossy compression can drop the one line that matters. If an answer looks wrong after reading a big log or JSON, retrieve the original (`headroom_retrieve`) before acting.
- Don't use it on sessions handling secrets or client data Dean hasn't cleared for an extra local proxy and cache.
