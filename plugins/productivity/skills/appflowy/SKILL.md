---
name: appflowy
description: "Use AppFlowy, the open-source Notion alternative (docs, wikis, databases, kanban, calendar, AI with optional local models), local-first on Dean's machine or synced via AppFlowy Cloud or a self-hosted server. Use when Dean wants a private notes/docs/wiki/project workspace, compares Notion, wants to self-host a team workspace, or mentions AppFlowy."
metadata:
  pricing: freemium
  cost: "Desktop app free and open source (AGPL); free Personal cloud plan (100 MB storage, 7 MB uploads); Pro $12/member/mo annual. Self-hosting AppFlowy Cloud is possible (check seat terms)."
  tags: [notes, docs, wiki, notion-alternative, local-first]
---

# AppFlowy

[AppFlowy-IO/AppFlowy](https://github.com/AppFlowy-IO/AppFlowy) (AGPL, Flutter + Rust) is a Notion-style workspace whose data lives on Dean's disk by default.

Note: repos like `AppFlowy-with-AppFlowy-Cloud-…` (a handful of stars) are third-party setup examples. Use the official AppFlowy and AppFlowy-Cloud repos and docs.

## Pick the setup

- **Local-only (free):** install the desktop app (appflowy.com, or GitHub releases) and use it without an account. Data stays local. Back up its data folder.
- **AppFlowy Cloud, Personal (free):** sync across devices and mobile, with tight limits (100 MB storage, 7 MB uploads, 7-day version history).
- **Pro ($12/member/month annual):** unlimited storage, forms and charts, 90-day history, team spaces and permissions.
- **Self-hosted AppFlowy Cloud:** the official [AppFlowy-Cloud](https://github.com/AppFlowy-IO/AppFlowy-Cloud) Docker deployment (AGPL) for data control. Check the current docs for seat or feature terms on self-hosted plans before rolling it out to a team.
- Prices as of 2026-10-27; check appflowy.com/pricing.

## Using it

- Good for: personal knowledge base, client project wikis, meeting notes, lightweight task boards and databases.
- AI: AppFlowy AI (paid or limited on cloud), or **Local AI** with local models (pair with `ollama`) for private notes.
- Want to ask questions across docs, or publish an "ask our docs" bot? Export to Markdown and use `weknora`. For heavy project management (Gantt, time tracking), use `openproject`.

## Notion vs AppFlowy

AppFlowy wins on privacy, offline use and price. Notion still leads on integrations, polish, real-time collaboration at scale and its template ecosystem. Migrating: export Notion to Markdown/CSV, then import, and check databases and relations by hand.
