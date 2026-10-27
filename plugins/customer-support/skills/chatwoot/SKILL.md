---
name: chatwoot
description: Set up and use Chatwoot, the open-source Intercom/Zendesk alternative: a live chat widget for websites plus a shared support inbox for email, WhatsApp, Instagram, Facebook, Telegram and SMS, with a help center and canned replies. Use when Dean wants live chat or a support widget on Dean's or a client's site, a shared inbox for customer messages, a help center or FAQ portal, or compares Intercom, Crisp, Zendesk or Tidio.
---

# Chatwoot

[chatwoot/chatwoot](https://github.com/chatwoot/chatwoot) is a Rails + Vue app. Core code is MIT; the `enterprise/` folder is under a commercial license and needs a paid license for production use.

## Pick the edition

- **Cloud "Hacker" plan: free for up to 2 agents** with 500 conversations/month and 30-day retention, but no Captain AI, help center, teams or automation. Good for a small client site or trying it out.
- **Cloud Startups ($19/agent/month) or Business ($39/agent/month)** add the help center, all channels, AI credits, automation and teams.
- **Self-hosted Community: free, unlimited agents and conversations** for the MIT features: widget, inbox, channels, canned responses, reports and the help center. No Captain AI, custom branding, roles/permissions, SSO or SLAs. Those are self-hosted Premium ($19/agent/month) or Enterprise ($99/agent/month).
- Prices as of 2026-10-27; check chatwoot.com/pricing.
- For an agency: one self-hosted instance can host several client **accounts** (separate inboxes and agents per client). Check the current docs on multi-account setup.

## Self-host (Community)

- Follow the official Docker or Linux guide on chatwoot.com/docs (self-hosted section), not third-party scripts.
- It needs Linux with **4 GB RAM and 2 CPUs minimum** for production, PostgreSQL, Redis, S3-compatible storage for attachments, SMTP for email, and HTTPS on a domain.
- Change all secrets, disable public sign-up after creating the admin account, and set up backups for Postgres and storage.
- Never enable or copy code from `enterprise/` in production without a license.

## Add the widget to a site

- Create a **Website inbox** and copy its widget script or website token.
- Next.js: load the SDK script once, client-side (for example with `next/script` and `strategy="lazyOnload"`), in the root layout.
- Match the site: set the widget color, position, greeting and bubble style in the inbox settings. Hide it on pages where it gets in the way (checkout steps, full-screen tools).
- Identify signed-in users with the SDK's `setUser`, and use **identity validation (HMAC)**, computing the hash server-side, so visitors can't impersonate others.
- Set business hours and an away message. Collect an email before chat if no one answers live.
- Performance: lazy-load it so it doesn't slow the first paint, and check Lighthouse afterwards.

## Working with it

- Canned responses for common questions, labels for routing, and the help center for FAQs (link articles in replies).
- API: use account API tokens for automation (creating contacts, syncing with a CRM, posting messages from other systems). Keep tokens server-side and read the current API docs before coding.
- AI: Captain (OpenAI-based) is paid. For AI answers grounded in a client's own docs, a **weknora** knowledge base is an option, used alongside or connected through the API.

## Don't

- Don't put agent or API tokens in client-side code.
- Don't log or forward chat transcripts containing personal data without the client's privacy policy covering it.
