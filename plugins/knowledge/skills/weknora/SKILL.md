---
name: weknora
description: "Set up and use WeKnora, Tencent's open-source self-hosted AI knowledge base (RAG Q&A with citations, agents, auto-wiki and knowledge graph over uploaded documents). Use when Dean wants to chat with or search a set of documents, build a knowledge base, add an \"ask our docs\" chatbot or embed widget to a client website, connect project or client docs to Claude Code over MCP, or mentions WeKnora, RAG, or Notion AI Q&A."
metadata:
  pricing: free-self-host
  cost: "Free (MIT, self-host); bring your own model API (paid per token) or free local models; needs a server."
  tags: [rag, knowledge-base, chatbot, mcp, self-hosted]
---

# WeKnora

[Tencent/WeKnora](https://github.com/Tencent/WeKnora) (MIT) ingests documents (PDF, Office files, web pages, Notion/Feishu sources, images) and answers questions over them with citations. It also runs a ReAct agent and builds a wiki and knowledge graph. It's a knowledge base, **not** a notes/docs editor: it replaces Notion AI's Q&A, not Notion.

## Costs

- **Models aren't included, and aren't covered by Dean's Claude subscription.** Pick per knowledge base:
  - an API key (Anthropic, OpenAI, DeepSeek…; pay per token)
  - local models through Ollama ($0, but needs RAM, and a GPU helps)
- **Embeddings** are needed for every document: a cheap API embedding model, or a local one via Ollama.
- Estimate the cost before ingesting large document sets on paid models.

## Set up

**Standard (Docker Compose, all features):**
```bash
git clone https://github.com/Tencent/WeKnora.git && cd WeKnora
git checkout v0.8.3            # pin a reviewed release; update deliberately
cp .env.example .env           # read the comments and set models, secrets, ports
docker compose pull && docker compose up -d
```
Web UI at http://localhost (onboarding wizard), API at :8080, and Langfuse tracing at :3000 (self-hosted). Optional services: `--profile neo4j` (knowledge graph), `--profile minio` (file storage).
- Upgrades: set `WEKNORA_VERSION` in `.env`, then `docker compose pull && docker compose up -d`. Read the release's upgrade notes first.
- Local models: start Ollama first (see the `ollama` skill, local-ai plugin) and set `OLLAMA_BASE_URL`. See WeKnora's configuration docs for the embedding model name and RAM notes.

**Lite single binary** (SQLite, no Postgres or Redis): for a laptop or a small VPS. See `docs/LITE.md` in the repo for what's missing compared to the standard setup.

Keys go into `.env` or the UI only, never into git. Change default secrets before exposing it beyond localhost, and put HTTPS and auth in front.

## Use cases for Dean

### 1. Project or client docs in Claude Code (MCP)
WeKnora's built-in MCP server exposes per-workspace endpoints at `/mcp/<endpoint_id>` over Streamable HTTP. Each has its own token, knowledge-base scope and rate limit.
- Create an endpoint in WeKnora scoped to just the knowledge bases needed. Read-only use is the default intent.
- Add it to Claude Code: `claude mcp add --transport http weknora <url>/mcp/<endpoint_id> --header "Authorization: Bearer <token>"`. Check the exact auth header in WeKnora's MCP docs. Dean pastes the token; never print or commit it.
- Then Claude can search briefs, specs and past decisions while it works, citing which document it used.

### 2. "Ask us" chatbot on a client website
- Make a knowledge base per client (services, FAQ, policies, pricing docs), then use WeKnora's website **embed widget** in secure mode (token exchange plus rate limits).
- Style the widget to match the site (see `dean-design-taste` / `editorial-themes`). It must cite sources and say "I don't know" rather than guess.
- Check the client's documents for anything private before ingesting. Everything in the knowledge base can surface in answers.
- Hosting: the client's own server or Dean's VPS, not a laptop. Budget model costs per conversation and set rate limits.

### 3. Personal research base
Upload PDFs, docs and saved pages, then ask questions with citations. Use the auto-wiki to get an overview of a large set.

## Good habits

- One knowledge base per purpose or client. Don't mix clients.
- Prefer smaller, clean documents. Review chunking and parsing on a sample before bulk upload.
- Test with 10–20 real questions and check the citations before calling it ready.
- Enable MCP human-in-the-loop approval for any tool that can write or act.
