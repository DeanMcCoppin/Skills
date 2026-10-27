# Source

- Tool: https://github.com/Tencent/WeKnora (Tencent; MIT, with third-party components under their own licenses)
- This skill: Dean (original), written with Claude. Setup facts are from the README (release v0.8.3, tag 3e22822). No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (README, LICENSE, feature/release notes). The codebase, compose file and `.env.example` weren't audited line by line; read `.env.example` comments on first setup.

## Notes

- Verdict: a mature, free, self-hosted knowledge base. The best fits for Dean are (1) client-site "ask our docs" chatbots via the embed widget and (2) feeding project or client docs to Claude Code over MCP. The "replaces Notion AI" pitch is only half true: it replaces the Q&A, not the editor.
- Cost reality: free software, but you bring the models (API tokens or local Ollama) plus embeddings, and you need a server for client use. The promo's "$180/mo saved" assumes a team Notion AI plan.
- Why it's credible: Tencent, MIT, ~35k stars, ~3,800 commits, frequent releases (v0.8.3 on 2026-10-14), a security policy, Helm/Docker/Lite deploys.
- Good at:
  - hybrid search with citations, multimodal parsing (PDF/Office/images)
  - ReAct agent with tools and sandboxes
  - auto-wiki and knowledge graph
  - 29 model vendors including Anthropic and Ollama
  - built-in MCP server (scoped tokens), embed widget
  - IM channels (Slack, Telegram, WeCom, Feishu)
  - RBAC workspaces, audit logs
- Weak at / risks:
  - heavy standard stack (Postgres/pgvector, Redis, optional Neo4j/MinIO)
  - many moving parts to secure when exposed publicly
  - some docs and ecosystem lean Chinese-platform (WeChat, Feishu)
  - the agent sandbox and browser control are powerful: keep tool approval on
  - not a writing or notes app
- Alternatives:
  - Notion AI (if you live in Notion)
  - other self-hosted RAG UIs (e.g. AnythingLLM, Dify, Open WebUI knowledge)
  - Claude Projects (upload files, no self-hosting, uses the Claude subscription)
  - a custom RAG with pgvector for full control
- Review: before moving the pinned release, read its upgrade notes and changes to MCP and auth.
