# Source

- Tool: https://github.com/ollama/ollama
- Author: Ollama Inc. and contributors
- License: MIT
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (LICENSE, README, Claude Code integration docs, pricing page).

## Notes

- Verdict: the easiest way to run open models locally; the backbone for private or zero-cost AI in other tools. Not a replacement for Claude on serious coding.
- Good at:
  - one-command model downloads
  - OpenAI/Anthropic-compatible local API
  - embeddings
  - `ollama launch` integrations (Claude Code, Codex…)
  - optional cloud models
  - huge model catalog
- Weak at / risks:
  - local model quality and speed depend on hardware and are far below frontier models for agentic work
  - no auth on the local API
  - big disk usage
  - the Linux installer is `curl | sh` (read it first)
  - each model's own license applies
- Alternatives: LM Studio (GUI, free); llama.cpp directly; vLLM (servers); paid APIs (Anthropic) for quality
