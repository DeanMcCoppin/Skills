---
name: refero
description: "Research real product UI before designing, with Refero: 145,000+ screens and 12,000+ user flows from shipped web and iOS apps, plus Refero Styles (colors, typography, spacing and components extracted from real websites, exportable as DESIGN.md) and the Refero MCP for Claude Code. Use when Dean starts designing a screen, flow or landing page and wants proven references, needs patterns for onboarding, pricing, empty states, settings or paywalls, wants a style starting point, or mentions Refero."
metadata:
  pricing: freemium
  cost: "Free tier sees ~3% of the library; Pro $10/mo billed annually ($120/yr), Team $12/seat/mo; Refero MCP and Refero Skill are Pro features (as of 2026-10-27)."
  tags: [design-research, ui-patterns, references, mcp, design-tokens]
---

# Refero

[Refero](https://refero.design) is a curated library of real product interfaces with structured metadata (UX and UI patterns, layouts). **Refero Styles** (beta, at styles.refero.design) extracts design systems from real sites, each with a DESIGN.md an agent can follow.

## When to use it

Use it **before** designing anything non-trivial: onboarding, pricing, checkout, dashboards, settings, empty or error states, or a landing page for a new industry. Studying 5–10 real solutions beats designing in a vacuum, and is the opposite of the generic AI look `dean-design-taste` bans.

## Setup (Pro)

- MCP and the agent skill need **Refero Pro** ($10/month billed annually). The free tier shows about 3% of the library.
- Connect the **Refero MCP** via refero.design/mcp (pick Claude Code there). On the first call, a browser window opens to sign in to Refero.
- **Refero Skill:** `npx skills add https://github.com/referodesign/refero_skill`. The repo has no license file, so it isn't vendored here. Review it before installing it per project.

## How to use references (without copying)

1. Search by pattern and industry ("pricing pages for dev tools", "fintech onboarding flows"), and collect 5–10 references.
2. Extract **patterns**, not pixels: information order, hierarchy, how many steps, what reassures the user, how errors and empty states are handled.
3. Design Dean's own version with the project's tokens, type and `editorial-themes` / `dean-design-taste` direction.
4. **Refero Styles / DESIGN.md:** use them as a starting point or for vocabulary. **Don't clone another company's brand** (exact palette plus type plus layout) for a client. Mix references, and change at least the palette, type pairing and signature details.

## Notes

- Pairs with `penpot` (references next to the design), `design-system` (turn chosen patterns into tokens) and `component-libraries` (build them fast).
- Free alternatives for inspiration: `design-inspiration` (landings.dev, rebrand.gallery, ilovecreatives), Mobbin's free tier, Dribbble (less realistic).
