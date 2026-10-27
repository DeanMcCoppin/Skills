---
name: ollama
description: "Run open AI models locally (and optionally in Ollama's cloud) with Ollama - Qwen, DeepSeek, gpt-oss, Gemma, Kimi, GLM and more - for private, offline or zero-cost AI: embeddings and local LLMs for WeKnora, AppFlowy and other tools, OpenAI/Anthropic-compatible local APIs for apps, and even running Claude Code against local models. Use when Dean wants local or offline AI, to avoid API costs for a task, to wire a local model into a tool or app, or mentions Ollama."
metadata:
  pricing: free
  cost: "Free (MIT); local models unlimited on your hardware. Optional Ollama cloud: pay-as-you-go, Pro $20/mo, Max $100/mo (as of 2026-10-27)."
  tags: [local-ai, llm, embeddings, privacy, ollama]
---

# Ollama

[ollama/ollama](https://github.com/ollama/ollama) (MIT) downloads and serves open models with one command, and exposes a local API at `http://localhost:11434` (its own API, plus OpenAI- and Anthropic-compatible endpoints).

## Install

- macOS/Windows: the app from ollama.com, or `brew install ollama` on macOS.
- Linux: the official script is `curl -fsSL https://ollama.com/install.sh | sh`. That's download-and-execute, so read the script first (or use your distro package or Docker `ollama/ollama`).
- Then: `ollama pull qwen3.5` (or another model), and `ollama run qwen3.5` to chat.

**Pick models by hardware.** Small models (3–8B) run on laptops; 14–32B needs about 16–32GB of RAM or VRAM; bigger ones need a serious GPU, or use the `:cloud` variants. Check each model's license on ollama.com before commercial use.

## Uses for Dean

- **Local models for other tools:** embeddings and chat for `weknora` (set `OLLAMA_BASE_URL`), AppFlowy's local AI, OpenWhispr's AI cleanup, n8n AI nodes. Common embedding models: `nomic-embed-text`, `bge-m3`.
- **In apps:** point any OpenAI-compatible SDK at `http://localhost:11434/v1` for private prototypes, offline demos or bulk jobs (classification, summaries, alt text) where API costs add up.
- **Claude Code on local or open models:** `ollama launch claude`, or manually:

  ```bash
  export ANTHROPIC_BASE_URL=http://localhost:11434 ANTHROPIC_AUTH_TOKEN=ollama ANTHROPIC_API_KEY=""
  claude --model qwen3.5
  ```

  Set the context to 64k or more (`OLLAMA_CONTEXT_LENGTH=65536`). Be honest about quality: open local models are far weaker than Claude at agentic coding. Use this for offline work, privacy-sensitive repos or throwaway tasks, not as a replacement. `/status` confirms which backend is active. This doesn't use or affect Dean's Claude subscription.

## Rules

- Ollama listens on `127.0.0.1` with **no authentication**. Never expose it with `OLLAMA_HOST=0.0.0.0` on a public network without a reverse proxy and auth in front.
- `:cloud` models send prompts to Ollama's servers (they state no logging or training). Keep confidential client data on local models.
- Models are large (GBs each). `ollama list` and `ollama rm <model>` keep disk use in check.
