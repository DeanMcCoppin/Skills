---
name: cap
description: "Set up and use Cap, the open-source Loom alternative for screen recording: Instant mode (shareable link the moment you stop) and Studio mode (local editor with zooms, backgrounds, captions, 4K export). Use when Dean wants to record a screen walkthrough, demo, bug report or client update video, share a recording link, compares Loom, or mentions Cap."
metadata:
  pricing: freemium
  cost: "Free for personal use only; client/commercial work needs the $58 one-time (or $29/yr) license; Pro $12/mo."
  tags: [screen-recording, loom-alternative, video, async]
---

# Cap

[CapSoftware/Cap](https://github.com/CapSoftware/Cap) is a desktop app (Tauri/Rust) for macOS and Windows, plus a Next.js web app for sharing. It's licensed AGPLv3 (some capture crates are MIT).

## License and plan: check this first

- **Free plan = personal use only.** You get unlimited local recording, Studio mode, 4K/60 export, and share links up to 5 minutes.
- **Client or business work is commercial use:** it needs the **Desktop License** ($29/year or $58 once), which also gives 20 cloud links/month (up to 5 min each).
- **Cap Pro ($12/month, ~$8.16/month billed yearly):** unlimited cloud storage and length, AI titles/summaries/chapters/transcripts, custom domain, password-protected links, viewer analytics, Loom importer, and your own S3 bucket or Google Drive.
- **Self-hosting** the sharing server (Docker Compose, or Railway/Coolify) keeps recordings on Dean's own S3-compatible storage (R2, B2, MinIO…), and the desktop app can point to it. The FAQ says self-hosting keeps all features. Check whether commercial use of the desktop app still needs a license when self-hosted.
- Prices as of 2026-10-27; check cap.so/pricing.

Recommendation for Dean: buy the **$58 one-time Desktop License** if recordings are mostly exported files or short links. Go Pro or self-host only if Dean shares many long client videos.

## Install

Download from cap.so/download or GitHub Releases. Grant **screen recording**, **microphone** and (optionally) **camera** permissions on first run.

## Recording well

- **Instant mode** for quick async updates, bug reports and replies to clients: the link is ready when recording stops.
- **Studio mode** for demos and portfolio or launch videos: auto-zoom on clicks, backgrounds and padding, cursor smoothing, captions, then 4K export.
- Keep videos short (1–3 min per topic). State the goal in the first 10 seconds, close unrelated tabs and notifications, use a clean browser profile, and bump the zoom level so text is readable.
- Hide secrets: no API keys, `.env` files, customer data or private dashboards on screen. Re-check before sharing.
- For websites: export MP4/WebM, compress, and embed with a poster frame (see the voicestudio/open-higgsfield export notes). Don't hotlink share-page URLs as video sources.

## Pairs with

- **openwhispr** to dictate the script or notes, **voicestudio** for a clean voiceover on Studio exports, **openproject** to attach walkthrough links to tasks.
