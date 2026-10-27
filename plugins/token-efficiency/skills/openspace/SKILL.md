---
name: openspace
description: "Use OpenSpace (HKUDS), a skill-management layer and MCP server that retrieves the right skill per task, records outcomes, and evolves skills from real runs - locally, with its public cloud for sharing kept off by default. Use when Dean wants agents to find skills automatically across a large library, measure which skills actually help, auto-improve skills from task traces, or mentions OpenSpace."
metadata:
  pricing: pay-per-use
  cost: "Software free (MIT). Its task execution and skill evolution call an LLM through your own API key (paid per token, or free with local Ollama models). Cloud sharing optional."
  tags: [skills, agents, mcp, skill-evolution, retrieval]
---

# OpenSpace

[HKUDS/OpenSpace](https://github.com/HKUDS/OpenSpace) (MIT, Python 3.12+) runs as an MCP server (`openspace-mcp`). It searches a skill library, delegates tasks (`execute_task`) to its own LLM loop, records what worked, and proposes improved skills.

## How it relates to this repo

**This marketplace stays the source of truth.** OpenSpace may *search* Dean's skills and *propose* evolved versions, but nothing it generates gets into `plugins/` without going through the **add-skill** review, the same as any import. Treat its suggestions as inbox items.

## Guardrails

- **Cloud off by default.** Don't set `OPENSPACE_CLOUD_MODE=live` or an `OPENSPACE_CLOUD_API_KEY` unless Dean decides to share. Its cloud receives telemetry-backed search, package pulls and **task-trace uploads**. Never upload traces from client projects (they contain code, paths and data).
- **Costs:** `execute_task` and evolution use the model in `OPENSPACE_MODEL` with `OPENSPACE_LLM_API_KEY` (Anthropic, OpenAI, OpenRouter, DeepSeek…), billed per token. Not covered by Dean's Claude subscription. Use a local `ollama/*` model to try it for free. Set limits and watch usage.
- Keys go into `openspace/.env` (Dean edits it), never into chat or the MCP config committed to a repo.
- The headline claims ("46% fewer tokens", "$11K earned in 6 hours") are the project's own and **unverified**. Measure on Dean's own tasks before relying on it.

## Setup (local only)

```bash
git clone --filter=blob:none --sparse https://github.com/HKUDS/OpenSpace.git && cd OpenSpace
git sparse-checkout set --no-cone '/*' '!/assets/'      # skips ~50 MB of images
git checkout <reviewed-commit>
python3.12 -m pip install -e .
openspace-mcp --help
```

Add it to Claude Code per project (stdio), with `OPENSPACE_WORKSPACE` set to the repo path and `OPENSPACE_HOST_SKILL_DIRS` pointing at the skill folders it may search. Point it at a **copy** or at `.claude/skills`, not directly at this repo's `plugins/` with write access. Give long tool calls a 600s timeout. Don't paste the README's "install OpenSpace for this host agent" prompt as-is: it lets the agent edit global configs, so do these steps deliberately.

## When it's worth it

Large skill libraries across many agents, or teams wanting outcome data per skill. For Dean's single marketplace, Claude Code's own skill matching plus good descriptions (this repo's rule) already covers retrieval, so try OpenSpace on a side project first.
