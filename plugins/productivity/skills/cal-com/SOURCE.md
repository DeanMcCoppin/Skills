# Source

- Tools: https://cal.com (cloud), https://github.com/calcom/cal.diy (community self-host fork, MIT), https://github.com/calcom/cal.com (main repo, open-core: AGPL + commercial `ee`)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (cal.diy README, cal.com pricing page). The embed and API details are general Cal.com usage; check the current docs before relying on specific options or endpoints.
- Dean's take: "this one I know, it's good."

## Notes

- Verdict: an excellent Calendly replacement. For Dean, use the **cloud free plan**: it's genuinely complete for one person. Self-host cal.diy only for data control or tinkering, not client production.
- Cost reality: free for individuals in the cloud; Teams $12/user/month, Organizations $28/user/month. The promo implies you need the repo to save money, but you don't: the cloud free tier already replaces paid Calendly for a solo user.
- About cal.diy: a fork of Cal.com with all enterprise code removed (no Teams, Organizations, Workflows, Insights, SSO). It's MIT, self-host only, its README calls it personal and non-production, and telemetry is on by default (`CALCOM_TELEMETRY_DISABLED=1` turns it off).
- Why it's credible: Cal.com is a well-funded company; the repo has ~49k stars and ~16.5k commits; it's widely used.
- Good at:
  - unlimited event types and calendar sync
  - payments (Stripe/PayPal)
  - 100+ integrations, Calendly import
  - polished React embeds (inline, popup, floating button)
  - API v2
  - open source
- Weak at / risks:
  - team scheduling features are paid
  - Cal.com branding on the free plan
  - self-hosting is real ops work (Postgres, SMTP, migrations)
  - the main repo's commercial `ee` code has separate license terms
  - ~1.2k open issues
- Alternatives:
  - Calendly (the paid incumbent)
  - Google Calendar appointment schedules (free with Workspace, basic)
  - TidyCal (one-time payment)
  - SavvyCal (paid, great UX)
- Pairs with: openproject (sync bookings into projects), the web-design skills (styling the embed).
