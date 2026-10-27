# Source

- Tool: https://github.com/plausible/analytics (CE deploy: https://github.com/plausible/community-edition)
- Author: Plausible Insights OÜ and contributors
- License: AGPLv3 (Community Edition)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (self-hosted vs cloud comparison page).

## Notes

- Verdict: the default analytics for Dean's and client sites: simple, cookieless, fast. Cloud for clients who need funnels or ecommerce; CE for Dean's own sites.
- Good at:
  - tiny script, no cookies
  - usually no consent banner
  - clear dashboard
  - custom events and goals
  - Search Console integration
  - EU hosting (cloud)
- Weak at / risks:
  - CE lacks funnels, journeys, ecommerce revenue and SSO
  - CE updates only twice a year
  - basic bot filtering on CE
  - ad blockers (use the proxy)
  - cloud pricing not verified here
- Alternatives: Google Analytics 4 (free, complex, consent needed); Umami (MIT, self-host); Fathom (paid, privacy-first); PostHog (product analytics)
