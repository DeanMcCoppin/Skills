# Source

- Tools:
  - Cult UI: https://www.cult-ui.com, https://github.com/nolly-studio/cult-ui (Nolly Studio / @nolansym; MIT)
  - Watermelon UI: https://ui.watermelon.sh, https://github.com/WatermelonCorp/watermelon-platform (WatermelonCorp; MIT)
  - Skiper UI: https://skiper-ui.com (Gxuri / Gurvinder Singh; license not published)
  - Componentry: https://componentry.dev, https://github.com/harshjdhv/componentry (Harsh Jadhav; MIT)
  - Aceternity UI: https://ui.aceternity.com (Manu Arora; custom licence: unlimited end products for yourself or clients, no redistribution, resale, or selling themes or templates)
  - Dotmatrix: https://dotmatrix.zzzzshawn.cloud, https://github.com/zzzzshawn/matrix (shawn / zzzzshawn; custom proprietary license allowing commercial use, but no publishing components as reusable or standalone or reselling them)
- This skill: Dean (original), written with Claude. No component code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (sites, Cult installation docs, Watermelon README at bba3511, Cult repo at 7f031dc; added later the same day: Componentry README and LICENSE, Aceternity pricing and licence pages, Dotmatrix site and LICENSE at e30b80a). Component source wasn't audited, so the skill makes Claude read each component before adding it.
- Dedupe decision: one hub skill for all copy-in component libraries instead of three near-identical skills. `bencho-blocks` and `bklit-charts` stay separate because their install flows and scope differ, and both are linked from the hub.

## Notes

- Verdict: Cult UI and Watermelon UI are the safe defaults (MIT, free, MCP available). Skiper UI is great for signature moments but needs a license check before client use.
- Skiper UI facts:
  - 106+ components on the site (the promo says 73+)
  - Premium is $129 one-time, and an "Exclusive" tier at $549 with Figma and templates is coming
  - no license on the site and no public repo found
  - a third-party listing (Tailkits) says free users must attribute, which is unverified
- Cult UI facts:
  - 154 components, "all free, MIT"
  - a separate paid product (AI SDK Agents blocks, one-time purchase)
  - an MCP server
- Aceternity UI facts:
  - free 100+ components
  - 1-year $169, lifetime $199, team (10) $1,590 (sale prices as shown)
  - "AI-ready prompts" are paid; MCP is free
  - its effects are widely copied, so restyle them for distinctiveness
- Componentry facts: about 53 components, Tailwind 4 and Framer Motion, MIT, ~465 GitHub stars (young).
- Dotmatrix facts: 55+ loaders on a shadcn registry; "Custom Proprietary License" (commercial use OK; no redistributing as reusable components).
- Watermelon UI facts:
  - React 19, Tailwind 4, Motion
  - components, blocks, dashboards and templates
  - a hosted MCP with no key
  - the promo says 260+ components (not verified)
- Good at: fast, distinctive components that stay editable; shadcn-native install; works with Dean's stack.
- Weak at / risks:
  - quality and accessibility vary per component
  - hard-coded styles need token mapping
  - mixing libraries fragments the visual language
  - Skiper's licensing is unclear
- Alternatives: Magic UI and Aceternity UI (popular shadcn-style libraries, not reviewed here); plain shadcn/ui + Radix + the `motion` skill for custom work.
