# Source

- Tool: https://github.com/n8n-io/n8n
- Author: n8n GmbH and contributors
- License: Sustainable Use License (fair-code, not OSI open source); `.ee` files under the n8n Enterprise License
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (LICENSE.md).

## Notes

- Verdict: the strongest self-hostable Zapier/Make alternative for a technical user. Free self-host for your own and clients' internal use; check the license before running it as a service for multiple clients.
- Good at:
  - 400+ integrations
  - code nodes (JS/Python)
  - webhooks and cron
  - AI agent nodes (Anthropic, OpenAI, Ollama)
  - MCP server trigger
  - unlimited executions self-hosted
- Weak at / risks:
  - not open source: SUL forbids selling or hosting n8n for others
  - Enterprise features are paid
  - self-hosting needs backups and the encryption key kept safe
  - workflows can sprawl, so document them
- Alternatives: Zapier / Make (hosted, paid per task); Activepieces (MIT, simpler); Windmill (AGPL, code-first); plain cron + scripts
