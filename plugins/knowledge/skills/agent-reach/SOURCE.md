# Source

- Tool: https://github.com/Panniantong/Agent-Reach (Panniantong / "Agent Eyes"; MIT, Copyright (c) 2025 Agent Eyes)
- This skill: Dean (original), written with Claude. Upstream's own skill (`agent_reach/skill/SKILL_en.md`) wasn't vendored: it covers login and setup flows Dean chose not to use. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit 14c2134 (v1.6.0): README_en, docs/install.md, the skill header, CLI commands, `runtime/manage.py` (skill linking), `runtime/tools.py` and `update_notice.py` (downloads and network), grep of all channels for hosts. Not a full audit.
- Flags raised (Dean chose "public channels only" on 2026-10-27):
  - **Credential handling**: login channels copy the site's cookies from Dean's Chrome into Agent Reach's own browser (README: "that site's login is copied over from your Chrome").
  - Terms of service / account risk: automated access to logged-in X, Reddit, LinkedIn, Instagram, Facebook; the README itself recommends a secondary account. Sponsors include residential-proxy and scraping services.
  - Install from `releases/latest` (unpinned); uv via `curl -LsSf https://astral.sh/uv/install.sh | sh`; `tools.py` can download Node.js and uv itself; some channels install third-party tools (OpenCLI from `releases/latest`, a pinned boss-agent-cli).
  - `setup` links its skill into global skill folders of every detected agent.
  - The `web` channel uses third-party hosted services: Exa MCP (`mcp.exa.ai`) for search, Jina Reader for reading pages, so queries and URLs leave the machine.
  - Update check calls the GitHub releases API. No telemetry found. `gh` is run with `GH_TELEMETRY=false`.

## Notes

- Verdict: useful for reading public social content and video transcripts when WebFetch falls short; the login channels are where the risk is, so they're off by Dean's rule.
- Good at: one JSON interface across many platforms, automatic fallbacks, read-only by design, clean uninstall, Chinese platforms.
- Weak at / risks: X, Reddit and Instagram mostly need login for anything beyond public pages, so results without login are limited; fast-moving (1.6 was a big rewrite); third-party star counts vary (53k–79k).
- Alternatives: `yt-dlp` (YouTube subtitles and media), WebFetch, RSS feeds, official APIs (Reddit API, X API, paid) for anything at scale or for clients.
- Filed in knowledge (getting outside content in front of the agent), not seo or productivity.
