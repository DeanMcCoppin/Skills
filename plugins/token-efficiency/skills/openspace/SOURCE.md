# Source

- Tool: https://github.com/HKUDS/OpenSpace
- Author: HKUDS
- License: MIT
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at 3827781 (LICENSE, README quick start and agent-install prompt, .env.example).
- Added at Dean's request despite the caveats.

## Notes

- Verdict: ambitious skill retrieval and evolution layer, but it overlaps with this marketplace, sends telemetry and traces to its cloud when enabled, and its savings claims are unverified. Try it local-only on a side project.
- Good at:
  - skill search with embeddings and reranking
  - outcome tracking per skill
  - evolution proposals
  - MCP server
  - Ollama support
- Weak at / risks:
  - overlap with this repo's own flow
  - cloud telemetry and task-trace uploads (keep cloud off)
  - LLM costs for execute_task and evolution
  - heavy repo (Python 3.12, ~50 MB of assets)
  - the agent-install prompt edits global configs
  - marketing claims ($11K in 6 hours, 46% fewer tokens) unverified
- Alternatives: this repo's add-skill flow plus good descriptions; `strategic-compact` and `karpathy-guidelines` for actual token and rework savings
