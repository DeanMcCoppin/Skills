# Source

- Tool: https://github.com/chatwoot/chatwoot (Chatwoot Inc.; MIT outside `enterprise/`, commercial Enterprise License inside it)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (GitHub page, LICENSE and enterprise/LICENSE, cloud and self-hosted pricing pages). The widget SDK details are general Chatwoot usage; check the current docs.

## Notes

- Verdict: a mature, free self-hosted Intercom replacement for live chat plus a shared inbox. The best fit is client sites (one instance, an account per client) or a small cloud setup on the free 2-agent plan. The AI features (Captain) are paid.
- Cost reality:
  - Self-hosted Community is free with unlimited agents, but you run a 4 GB+ server.
  - The cloud free plan allows 2 agents and 500 conversations a month.
  - Paid plans are $19–$99/agent/month.
  - The promo's "$39/mo saved" roughly matches one Intercom seat; Intercom's AI and seats cost more at scale (not verified today).
- Why it's credible: an established company (since 2017), ~38k stars, ~7k commits, widely self-hosted, with Docker/Kubernetes/Heroku deploys.
- Good at:
  - polished website widget, omnichannel inbox (email, WhatsApp, Facebook, Instagram, Telegram, Line, SMS)
  - help center, canned responses, private notes, auto-assignment, labels
  - reports, API and webhooks
  - multiple accounts per instance
- Weak at / risks:
  - Captain AI, branding removal, roles, SSO and SLAs are paid (self-hosted Premium/Enterprise)
  - the `enterprise/` code is not free to use in production
  - real ops work: Postgres, Redis, S3, SMTP, upgrades
  - WhatsApp needs Meta Business API setup and fees
  - ~1.1k open issues
- Alternatives:
  - Intercom (best AI, expensive)
  - Crisp (cheap hosted, free tier)
  - Tidio (hosted, small-business focus)
  - Papercups (open source, inactive)
  - WeKnora's embed widget (AI document Q&A rather than human support)
- Review: before upgrading, check which features moved between Community and paid.
