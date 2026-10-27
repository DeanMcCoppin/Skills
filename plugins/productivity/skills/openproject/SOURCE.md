# Source

- Tool: https://github.com/opf/openproject (OpenProject GmbH and contributors; GPL-3.0)
- This skill: Dean (original), written with Claude. No code copied. API usage is from OpenProject's public API v3 conventions. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (GitHub page, pricing page). The install steps point to the official guide rather than pinning commands, because they change between major versions. The RAM figure is approximate; check the current requirements.

## Notes

- Verdict: a mature, trustworthy, free self-hosted PM suite for teams and agencies. "Asana killer" oversells it: it matches Asana's features, but feels more like Jira/MS Project, and it's overkill for solo work.
- Cost reality: Community is free (you run the server). Enterprise is €5.95–15.95/user/month with a 25-user minimum, so it isn't for small teams. The promo's "$215/mo saved" assumes a paid team Asana plan.
- Why it's credible: GPL-3.0, ~16.7k stars, ~117k commits, 15+ years old, run by a company with commercial support, regular releases.
- Good at:
  - work packages with types, workflows and custom fields
  - Gantt scheduling, Kanban/Scrum boards
  - time and cost tracking and budgets
  - wiki, meetings, forums
  - GitHub/GitLab and Nextcloud integrations
  - REST API v3 on Community
- Weak at / risks:
  - heavy (Rails + Postgres, about 4 GB+ RAM)
  - a denser UI than Asana
  - several things Asana users expect are Enterprise-only (team planner, resource/portfolio management, multiple sprints, SSO, external sharing, the MCP server)
  - GPL: fine to use, and you only share source if you distribute a modified version
- Alternatives:
  - GitHub Projects (free, next to code; best for solo dev)
  - Linear (paid, fast)
  - Plane (open source, Linear-like, lighter)
  - Vikunja (tiny self-hosted to-dos)
  - Asana itself (best UX)
- Review: on major upgrades, re-check which features moved between Community and Enterprise.
