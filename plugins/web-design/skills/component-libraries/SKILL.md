---
name: component-libraries
description: "Pick and install ready-made animated React components from shadcn-compatible libraries - Cult UI (154 free MIT components with personality), Watermelon UI (large MIT catalogue of components, blocks, dashboards and templates, with MCP), Skiper UI (uncommon showpiece components, free + premium) and Bencho (micro-interactions) - then fit them to the project. Use when Dean wants a fancier button, card, hero, text effect, nav, dock, dashboard block or other component than plain shadcn, asks which component library to use, or mentions Cult UI, Watermelon, Skiper or similar registries."
metadata:
  pricing: freemium
  cost: "Cult UI and Watermelon UI free (MIT); Skiper UI free + Premium $129 one-time (license unstated); Bencho free + Pro €79/yr. Prices as of 2026-10-27."
  tags: [shadcn, components, react, framer-motion, ui-library]
---

# Component libraries

All of these install with the **shadcn CLI**, which copies the component source into the project. You own and edit the code, so treat it as your code: read it, fit it, test it.

## Which one?

| Library | Best for | License and cost | Install |
| --- | --- | --- | --- |
| **[Cult UI](https://www.cult-ui.com)** | Animated components with personality (buttons, cards, inputs, text effects, docks), plus AI-SDK-style blocks | **MIT, free** (154 components) | `npx shadcn@latest add @cult-ui/<name>` |
| **[Watermelon UI](https://ui.watermelon.sh)** | Breadth: a large catalogue of production-ready components, plus blocks, dashboards and templates (React 19, Tailwind v4, Motion) | **MIT, free** | `npx shadcn@latest add https://registry.watermelon.sh/r/<name>.json` |
| **[Skiper UI](https://skiper-ui.com)** | Uncommon, showy one-off components for a signature moment (single file, no extra packages; Next.js + Motion) | Free + **Premium $129 one-time**. **License not published**, so check before client use (see below) | `npx shadcn add @skiper-ui/<name>` (for example `skiper40`) |
| **Bencho** | Tactile micro-interactions and UI sounds | MIT free tier, Pro €79/yr | See the `bencho-blocks` skill (copied from its repo, not a registry) |
| **Bklit** | Charts | MIT, free | See the `bklit-charts` skill |

Default order for Dean: **plain shadcn/Radix for structure → Cult or Watermelon for personality → Skiper or Bencho for one signature moment per page.**

If an older shadcn CLI can't resolve a namespace, add it to `components.json` `registries`, e.g. `"@cult-ui": "https://www.cult-ui.com/r/{name}.json"`.

### MCP servers (optional)

They let Claude search the catalogues and get install commands directly:
- Watermelon (hosted, no API key): `claude mcp add --transport http watermelon https://mcp.watermelon.sh/mcp`
- Cult UI: see cult-ui.com/docs/mcp-server.

Add them per project, only when doing heavy UI work.

## Before adding a component

1. **Check the license and tier.** Free MIT components are fine anywhere. Premium or paid items stay in Dean's own projects and are never committed to public repos or to this skills repo. **Skiper UI:** its site doesn't publish a license, and a third-party listing claims free components require attribution. Until confirmed, ask Dean before using Skiper components in client work, or credit Skiper UI in the project.
2. **Read the code it installs.** Look at new dependencies, network calls (there should be none), `"use client"`, and size.
3. **Fit it to the project:**
   - Map hard-coded colors, radii and shadows to the project's tokens (`dean-design-taste`), and drop any default purple gradients.
   - Imports: prefer `motion/react`; don't mix `framer-motion` and `motion` in one tree (see the `motion` skill).
   - Add reduced-motion fallbacks, keyboard and focus support, labels and contrast (see `accessibility`). Showy components often skip these.
   - Lazy-load heavy ones below the fold.
4. **Use them sparingly.** One or two personality pieces per page. Ten flashy components from three libraries make a site look like a demo reel, not a brand. Stay consistent with one library's visual language per project where possible.
