---
name: design-md
description: "Write and maintain a DESIGN.md (Google Stitch's plain-Markdown design-system format: YAML tokens for colors, type, spacing, radii plus prose rules) at the root of each project so every agent builds consistent UI, using VoltAgent's Awesome DESIGN.md collection (84 analyses of sites like Linear, Stripe, Vercel, Notion) as reference, never as a brand clone. Use when Dean starts a project's design system, wants agents to stay on-brand, asks for a site that feels like a known product, or mentions DESIGN.md or awesome-design-md."
metadata:
  pricing: free
  cost: "Free. The collection is MIT; getdesign.md offers paid custom requests."
  tags: [design-system, design-tokens, design-md, consistency, references]
---

# DESIGN.md

A `DESIGN.md` in the project root tells any agent how the product should look, the way `CLAUDE.md`/`AGENTS.md` say how to build it. Format (from [Google Stitch](https://stitch.withgoogle.com/docs/design-md/overview/)): YAML frontmatter with tokens (`colors`, `typography`, spacing, radii, shadows), then prose sections such as visual theme, color roles, typography rules, components, layout, depth, do's and don'ts, responsive behavior.

## Write one per project

1. Start from `dean-design-taste` (stack, motion and house rules) and the client's brand: logo colors, fonts they own, existing site.
2. Fill the tokens with **real values** (hex, font stacks, px/rem scales) and map them to Tailwind theme variables, so `DESIGN.md` and the code agree.
3. Prose: say what the brand *is* and the few decisions that make it recognizable (one accent, one display face, how sections separate). Short beats complete.
4. Add `See DESIGN.md before any UI work` to the project's `CLAUDE.md`.
5. Update it when the design changes; `design-system` audits code against it.

## Using the Awesome DESIGN.md collection

[VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) (MIT) holds DESIGN.md analyses "inspired by" Linear, Stripe, Vercel, Notion, Supabase, Raycast, Apple and ~80 more. Use them to:
- learn how good systems state their rules (copy the **structure**, not the brand)
- answer "make it feel like Linear" by borrowing principles (density, contrast, motion), then expressing them in the client's own colors and type

Rules:
- **Never ship a client site that copies another company's look** (palette + type + layout of Stripe is a trade-dress problem, and bad work). Same rule as `refero`.
- Their font stacks name commercial fonts (Söhne, SF Pro and others). Don't use a font the client hasn't licensed; substitute a free one.
- Files are analyses by third parties, not the brands' official systems, and some now only link to getdesign.md. Check values before relying on them.
