---
name: cal-com
description: "Set up scheduling with Cal.com (the open-source Calendly alternative) and add booking to websites: event types, availability, calendar sync, payments, and inline/popup booking embeds in React/Next.js sites. Use when Dean needs a booking or scheduling page, wants \"book a call\" or appointment booking on Dean's or a client's site, compares Calendly, or mentions Cal.com or cal.diy."
metadata:
  pricing: freemium
  cost: "Cloud free plan for 1 user; Teams $12/user/mo; self-hosted cal.diy is free (MIT)."
  tags: [scheduling, booking, embeds, calendly-alternative]
---

# Cal.com

## Pick the edition

- **Cal.com cloud, free plan (default for Dean):** $0 forever for 1 user, with unlimited event types and calendars, notifications, 100+ integrations, Stripe/PayPal payments and Calendly import. No server to run.
- **Teams ($12/user/month) or Organizations ($28/user/month):** only for round-robin or collective team booking, routing forms, removing Cal.com branding, SSO. Prices as of 2026-10-27; check cal.com/pricing.
- **Self-hosted [cal.diy](https://github.com/calcom/cal.diy) (MIT):** a community fork with **all commercial code removed**: no Teams, Organizations, Workflows, Insights or SSO. Its own README recommends it only for personal, non-production use. Choose it only for full data control or tinkering.
  - Setup: clone, `cp .env.example .env`, set `NEXTAUTH_SECRET` and `CALENDSO_ENCRYPTION_KEY` (`openssl rand -base64 32`), point `DATABASE_URL` at PostgreSQL 13+, then `docker compose up -d`, and the setup wizard runs on :3000.
  - Set `CALCOM_TELEMETRY_DISABLED=1`, because anonymous telemetry is on by default.
  - It also needs SMTP for emails, HTTPS, backups and migrations on upgrade.
- The main `calcom/cal.com` repo is open-core: AGPL plus a commercial `ee` folder. Don't self-host that for client work without checking the license.

## Set up an account (cloud)

1. Connect the calendars (Google/Outlook/Apple) and set working hours, buffers, minimum notice and a daily booking limit.
2. Create event types: a short "intro call" (15–30 min) and longer paid or working sessions. Add questions to the booking form (company, project, budget) and the location (Cal Video, Google Meet, Zoom, phone).
3. Payments: connect Stripe for paid sessions or deposits.
4. Import from Calendly if switching (one-click import).

## Add booking to a site

- React/Next.js: `npm i @calcom/embed-react`, then render `<Cal calLink="username/intro-call" />` inline, or use the floating-button or element-click popup embed. Load it client-side (`"use client"`).
- Match the site's design: set the brand color and theme (`light`/`dark`/`auto`) in the embed config, hide event-type details if the page already explains the offer, and set the layout (`month_view`, `week_view`, `column_view`).
- Put booking where intent is highest: the hero CTA ("Book a call"), the pricing page and the contact page. Don't make it the only way to get in touch.
- Prefill name and email from known data with embed config, and pass UTM/source parameters for tracking.
- Performance: lazy-load the embed below the fold, or open it on click, so it doesn't slow the first paint.
- Self-hosted cal.diy: point the embed at that instance's URL instead of cal.com.

## API

API v2 can list bookings, event types and availability (API key from settings; keep it server-side). Use it for dashboards or syncing bookings into OpenProject or a CRM. Check the current API docs for endpoints and versions before coding against them.

## Don't

- Don't put the API key in client-side code.
- Don't promise team features (round-robin, routing) on the free plan or on cal.diy.
