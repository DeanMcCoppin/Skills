---
name: n8n
description: "Build and self-host workflow automations with n8n (open-core Zapier/Make alternative, 400+ integrations, AI agent nodes, webhooks, cron) - form-to-CRM, notifications, content pipelines, AI enrichment, syncing tools - and have Claude design, validate and deploy workflows (importable JSON or the n8n-MCP server, with production guardrails and its telemetry off). Use when Dean wants to automate a process, connect apps or a website form to other tools, replace Zapier or Make, set up webhooks or scheduled jobs, or mentions n8n or n8n-MCP."
metadata:
  pricing: free-self-host
  cost: "Self-hosted Community edition free with unlimited executions (Sustainable Use License: internal business or personal use; Enterprise features paid). n8n Cloud is paid (check n8n.io/pricing)."
  tags: [automation, workflows, integrations, webhooks, self-hosted, mcp]
---

# n8n

[n8n-io/n8n](https://github.com/n8n-io/n8n) is a visual workflow builder with code nodes. It's **fair-code, not open source**: the Sustainable Use License.

## License: check first

- ✅ Dean's own business automations, personal use, and building workflows that run on **a client's own n8n instance** for that client's internal use.
- ❌ Selling n8n itself as a hosted service, or giving it to others commercially. For example, one n8n instance that Dean runs and charges several clients to use, or white-labeling it inside a product. That needs an n8n commercial or Embed license.
- Files with `.ee.` in the name or folder are Enterprise-licensed (SSO, advanced permissions, environments and so on).
- When unsure about a client setup, check n8n's license FAQ, or ask n8n.

## Self-host

```bash
docker volume create n8n_data
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

For anything real: Docker Compose with Postgres, a fixed `N8N_ENCRYPTION_KEY` (back it up, because credentials can't be decrypted without it), `WEBHOOK_URL` set to the public HTTPS URL, a reverse proxy with HTTPS, pinned image versions, and backups of the volume and database. Keep the editor behind auth (the owner account, plus SSO or a VPN for teams).

## Building workflows with Claude

- Claude can write workflows as **n8n JSON** for Dean to import (paste into the canvas or Import from file). Keep node types and versions to current, documented ones, and test with sample data before activating.
- Typical site automations: a contact or booking form (webhook) → validate → CRM, email or Slack → reply. Cal.com booking → OpenProject task. Chatwoot conversation → AI summary → ticket. New blog post → social posts.
- AI steps: n8n's AI Agent and LLM nodes work with Anthropic, OpenAI or local `ollama` models. Put limits on loops and tokens.
- n8n can expose workflows as MCP tools (MCP Server Trigger) for Claude Code. Treat them as privileged actions: scope them narrowly and require auth.

## n8n-MCP: Claude builds workflows directly

[czlonkowski/n8n-mcp](https://github.com/czlonkowski/n8n-mcp) (MIT) gives Claude docs for every n8n node, templates and a validator, and (with `N8N_API_URL` + `N8N_API_KEY`) tools to create, update and test workflows on an instance.

- **Telemetry is on by default and uploads sanitized workflow structures** (node types, names, connections, parameters with secret-looking fields redacted) plus the free-text change intent, to build ML datasets. Sanitizing is pattern-based. Turn it off before first use: `npx n8n-mcp telemetry disable`, or `N8N_MCP_TELEMETRY_DISABLED=true` for Docker or the MCP `env`.
- Self-host it (npx pinned to a version, or Docker with a pinned tag) with `MCP_MODE=stdio`. The hosted dashboard.n8n-mcp.com (free 100 calls/day) sends everything through their server; don't use it for client workflows.
- **Never point it at a production instance with write access.** Its own README says so. Use a dev/staging n8n, then export and import to production. For read-only use on prod, set `DISABLED_TOOLS` to the write tools (`n8n_create_workflow`, `n8n_update_full_workflow`, `n8n_update_partial_workflow`, `n8n_delete_workflow`, `n8n_autofix_workflow`, `n8n_deploy_template`, `n8n_test_workflow`, `n8n_manage_credentials`, `n8n_manage_datatable`) or use `DISABLED_TOOL_OPERATIONS`.
- The n8n API key goes in the MCP `env` from a secret store, never in a committed `.mcp.json`. Docs-only mode (no API URL or key) is enough for designing JSON.

## Rules

- Credentials live in n8n's credential store, never in node parameters, JSON exports or git. Strip credentials before sharing exported workflows.
- Webhooks: use authentication (header or basic auth), validate input, rate-limit public ones, and make them idempotent (retries happen).
- Add an error workflow (notify on failure), and log without personal data.
