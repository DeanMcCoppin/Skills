# Source

- Tool: https://github.com/every-app/open-seo (author: Ben Senescu / every-app; MIT)
- This skill: Dean (original), written with Claude. Setup facts are from the repo's README and `docs/SELF_HOSTING_DOCKER.md`. License: TODO (this repo has no LICENSE file yet).
- Their skills: 12 MIT skills in `plugins/openseo/skills/`, reviewed 2026-10-27 and clean (no outbound calls besides their MCP tools, no rule overrides, no credential handling). Linked rather than copied, by Dean's choice, so they stay current via their marketplace.
- Reviewed: 2026-10-27 (README, `.env.example`, plugin manifests, `.mcp.json`, all 12 SKILL.md files, Docker self-hosting doc).

## Notes

- Verdict: a strong, legit Semrush/Ahrefs replacement for small sites and client work at low or occasional volume. Self-host it and pay DataForSEO directly.
- Cost reality: the app is free, but data isn't: every lookup is a DataForSEO request. Hosted OpenSEO costs $10/mo plus 28% on data. Semrush starts around $140/mo (not verified today). It's much cheaper at low volume, but the gap narrows with heavy daily use.
- Why it's credible: MIT license, ~25k stars with ~900 commits, a security policy, Docker and Cloudflare deploy paths, and an official Claude Code plugin.
- Good at:
  - keyword research and clustering, competitor and backlink research
  - site audits with its own crawler
  - rank tracking, local SEO with Maps
  - AI-visibility (how brands show up in ChatGPT-style answers)
  - Search Console integration
  - MCP plus prebuilt agent skills, so Claude can do the research directly
- Weak at / risks:
  - data depth and history depend on DataForSEO, not Semrush's own databases
  - estimates vary by provider
  - self-hosting means running and updating Docker (4 GiB+ of memory)
  - their Claude plugin defaults to the hosted MCP (markup billing) unless the self-hosted server is used
  - reports carry a promo backlink line
  - younger project, so expect changes
- Alternatives: Semrush / Ahrefs (deepest data, expensive); Google Search Console (free, your own site only); calling DataForSEO directly (cheapest, no UI).
- Review: on updates, re-check their `.mcp.json` target and any new outbound calls in their skills.
