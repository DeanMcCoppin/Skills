# Source

- Tool: https://bencho.dev, free blocks at https://github.com/cabralorenzo/bencho (author: Lorenzo Cabra)
- Licenses: free blocks and sounds MIT (photos, name and logo excluded); Pro blocks under the Bencho Pro licence (commercial use OK, no redistribution as a kit or library).
- This skill: Dean (original), written with Claude. No block code is included in this repo. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit 30ab35a (README, package.json, site pricing/FAQ). Individual block source wasn't audited; the skill makes Claude read each block before copying it.

## Notes

- Verdict: a great source of high-quality micro-interactions for signature moments. The free 44 cover most needs; Pro is worth it only if Dean uses these often or wants the MCP.
- Good at: tactile, well-tuned interactions (drag physics, magnetic and liquid effects, loaders); every prop is tunable live on the site; framer-motion based like Dean's stack; free MIT tier; zero-asset synthesised sounds.
- Weak at / risks:
  - plain CSS plus its own `tokens.css`, not Tailwind, so each block needs token mapping
  - some blocks pull in heavy deps (`three`)
  - built for Vite/React, so Next.js needs `"use client"` and dynamic imports
  - a11y and reduced-motion support vary per block
  - easy to overuse
  - small repo (~58 stars, 22 commits) and a young project; the site counts differ (41 vs 44 free blocks)
  - free site membership and Pro upsell; Mobbin is a sponsor
- Alternatives: Magic UI, Aceternity UI, Motion Primitives (shadcn-style registries, Tailwind-native); building with Framer Motion directly for simple effects.
- Review: re-check the license and the free/Pro split before updating the pinned commit.
