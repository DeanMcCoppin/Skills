---
name: plausible
description: "Add privacy-friendly, cookieless web analytics with Plausible (Google Analytics alternative, tiny script, no cookie banner needed in most cases) to Dean's and client sites - self-hosted Community Edition or Plausible Cloud - including Next.js setup, custom events and goals, proxying, and reading traffic for SEO. Use when Dean wants analytics on a site, a GA replacement, GDPR-friendly tracking, conversion goals, or mentions Plausible."
metadata:
  pricing: free-self-host
  cost: "Community Edition free (AGPL, self-host, twice-yearly releases, some features cloud-only). Plausible Cloud is a paid subscription, EU-hosted (check plausible.io/#pricing)."
  tags: [analytics, privacy, gdpr, self-hosted, ga-alternative]
---

# Plausible

[plausible/analytics](https://github.com/plausible/analytics): simple, cookieless analytics with no personal data and a lightweight script.

## Cloud or Community Edition?

- **Cloud (paid):** zero ops, EU (Germany) hosting, frequent updates, advanced bot filtering. **Cloud-only:** funnels, user journeys, ecommerce revenue goals, SSO, sites API, Looker Studio connector. The right default for client sites that need those features or don't want a server.
- **Community Edition (free, AGPL):** self-host with the [plausible/community-edition](https://github.com/plausible/community-edition) Docker Compose setup (Plausible + Postgres + ClickHouse; give it about 2–4GB RAM). Long-term releases twice a year, community support, basic bot filtering. Good for Dean's own sites or several small sites on one server.
- **GDPR:** no cookies and no personal data means **no consent banner in most EU setups**, but check the client's jurisdiction and policies. For CE, compliance also depends on where you host it.

## Add it to a Next.js site

- Copy the site's script snippet from the site's settings in the Plausible dashboard (it's site-specific). In the App Router root layout, load it with `next/script` (`strategy="afterInteractive"`), or use the `next-plausible` package.
- **Proxy the script and event endpoint through the site's own domain** (Next.js rewrites or middleware) so ad blockers don't drop data. Plausible documents the proxy setup.
- Exclude dev, preview and staging, so only the production domain reports.

## Goals and events

- Track what matters for the business: contact or booking submits (Cal.com, forms), CTA clicks, outbound links, file downloads, 404s. Use custom events (`plausible('Signup', { props: { plan: 'pro' } })`) with a few meaningful props, never personal data.
- Name goals consistently (`Contact Submit`, `Book Call`), and add them as goals in the dashboard.
- For SEO: compare landing pages and sources with `openseo` keyword data and Google Search Console (connect it in Plausible for search queries).

## Don't

- Don't send emails, names or IDs in event props.
- Don't run GA and Plausible together without a reason, since it doubles the script cost and the consent questions.
