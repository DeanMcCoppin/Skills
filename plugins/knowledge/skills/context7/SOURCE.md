# Source

- Tool: https://github.com/upstash/context7 (Upstash; MIT for the client/MCP code; the docs index and API are a hosted Upstash service)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit 5c368c9 (README, setup and MCP docs).
- Flag raised: the promo's setup `claude mcp add context7 -- npx -y @upstash/context7-mcp@latest` is unpinned (supply-chain risk on every start). The skill pins or uses the remote server.

## Notes

- Verdict: worth enabling for web work. It directly fixes the "Claude writes last year's Next.js/Tailwind API" problem. Free tier is enough for one developer.
- Good at: fast-moving JS libraries, version-specific lookups, both CLI+skill and MCP modes.
- Weak at / risks: hosted dependency (queries go to Upstash), community-submitted docs can be incomplete or contain injected text, adds tokens per lookup, rate limits without a key.
- Alternatives: official `llms.txt` files and docs MCP servers some libraries ship (Supabase, Vercel, Mapbox); WebFetch of the docs page; `weknora` for private client docs.
- Filed in knowledge (feeding docs to agents over MCP) rather than token-efficiency.
