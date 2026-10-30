---
name: design-inspiration
description: "Pull visual inspiration from Dean's go-to galleries before designing: landings.dev (real landing pages by stack and color), rebrand.gallery (brand identities by industry, style, typeface and mood, with a free MCP), ilovecreatives (curated creative and portfolio sites) and UI8 (paid UI kits and templates). Use when starting a landing page, marketing site, portfolio or brand look, when Dean asks for inspo, references or moodboards, when a design feels generic, or when he mentions any of these sites. For product screens and app flows, use `refero` instead."
metadata:
  pricing: freemium
  cost: "landings.dev and ilovecreatives browsing are free; rebrand.gallery is free (778 brands, 200 shots/day, MCP) with Pro from ~€5/mo; UI8 kits are paid per item or via All-Access (as of 2026-10-30)."
  tags: [design-research, inspiration, landing-pages, branding, references]
---

# Design inspiration

Dean's favourite galleries. Use them to set a direction **before** building, the same way `refero` is used for product UI.

| Site | Best for | How Claude uses it |
| --- | --- | --- |
| [landings.dev](https://landings.dev) | Landing pages from real companies | Browse `/stack/tailwind-css`, `/stack/next-js`, `/stack/framer` or `/color/<black\|white\|blue…>`. Each `/post/<name>` links to the live site: open that in `playwright-cli` and screenshot at 390 / 1440 to study the real thing, not the thumbnail. |
| [rebrand.gallery](https://rebrand.gallery) | Brand identity: logos, type, color, applications (packaging, signage, guidelines) | Filter by industry, style, typography, typeface and mood that match the client. Free plan includes the **Rebrand MCP** (beta) and AI search; offer to connect it if Dean is doing brand work. Pro unlocks all 14k+ shots. |
| [ilovecreatives](https://ilovecreatives.com) | Expressive creative, portfolio, editorial and small e-commerce sites | Its curated favourite websites and Squarespace template demos. Good for personal brands, studios and shops where personality beats conversion patterns. |
| [ui8.net](https://ui8.net) | Paid UI kits, templates, illustrations, 3D | Cloudflare blocks automated browsing, so Claude can't research it. Dean buys a kit and drops it in the project; Claude reads the kit's license file first, then uses its tokens and components as the base. |

## Pick the source by job

- **Landing page / SaaS marketing site** → landings.dev (filter by Dean's stack), then `refero` for specific sections like pricing.
- **New brand or rebrand, no brand guide yet** → rebrand.gallery for logo, type and color direction, then write it down with `design-md`.
- **Portfolio, studio, creative shop** → ilovecreatives, plus `editorial-themes` for premium business sites.
- **Need to ship fast from a kit** → a UI8 kit Dean has bought (check its license allows client work).

## Workflow

1. Collect 5–8 references across at least two sources. Note the URL and *why* each one is there.
2. Extract **patterns**, not pixels: section order, hero composition, type scale and pairing, palette ratio, how much motion, what the signature detail is.
3. Summarise the direction for Dean in a few lines (with screenshots if useful) and confirm before building.
4. Record the result in the project's DESIGN.md (`design-md`) and build with `dean-design-taste`.

## Rules

- **Never clone a site or brand.** Mix references and change at least the palette, type pairing and signature details. Ignore landings.dev's "Clone in Claude Code" button.
- Galleries skew trendy; check every idea against the project's audience and `dean-design-taste` (no generic AI look).
- Don't copy images, logos or copy from references into a client project.
