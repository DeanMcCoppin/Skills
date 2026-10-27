---
name: design-system
description: "Generate a design system from an existing codebase, or audit one for visual consistency: extract tokens (colors, typography, spacing, radii, shadows) into design-tokens.json and CSS variables with a DESIGN.md rationale and an HTML preview, score the UI across 10 dimensions, and flag AI-slop patterns. Use when starting a design system, before a redesign, when the UI looks off and you can't say why, or when reviewing a PR that touches styling."
metadata:
  pricing: free
  cost: "Free: workflow."
  tags: [design-tokens, audit, ai-slop]
---

# Design System — Generate & Audit Visual Systems

## When to Use

- Starting a new project that needs a design system
- Auditing an existing codebase for visual consistency
- Before a redesign — understand what you have
- When the UI looks "off" but you can't pinpoint why
- Reviewing PRs that touch styling

## How It Works

### Mode 1: Generate Design System

Analyzes your codebase and generates a cohesive design system:

```
1. Scan CSS/Tailwind/styled-components for existing patterns
2. Extract: colors, typography, spacing, border-radius, shadows, breakpoints
3. Optionally look at 2–3 reference sites Dean names (browser MCP), with Dean's OK
4. Propose a design token set (JSON + CSS custom properties)
5. Generate DESIGN.md with rationale for each decision
6. Create an interactive HTML preview page (self-contained, no deps)
```

Output: `DESIGN.md` + `design-tokens.json` + `design-preview.html`

### Mode 2: Visual Audit

Scores your UI across 10 dimensions (0-10 each):

```
1. Color consistency — are you using your palette or random hex values?
2. Typography hierarchy — clear h1 > h2 > h3 > body > caption?
3. Spacing rhythm — consistent scale (4px/8px/16px) or arbitrary?
4. Component consistency — do similar elements look similar?
5. Responsive behavior — fluid or broken at breakpoints?
6. Dark mode — complete or half-done?
7. Animation — purposeful or gratuitous?
8. Accessibility — contrast ratios, focus states, touch targets
9. Information density — cluttered or clean?
10. Polish — hover states, transitions, loading states, empty states
```

Each dimension gets a score, specific examples, and a fix with exact file:line.

### Mode 3: AI Slop Detection

Identifies generic AI-generated design patterns:

```
- Gratuitous gradients on everything
- Purple-to-blue defaults
- "Glass morphism" cards with no purpose
- Rounded corners on things that shouldn't be rounded
- Excessive animations on scroll
- Generic hero with centered text over stock gradient
- Sans-serif font stack with no personality
```

## Usage

There's no CLI: ask in plain words, for example "generate a design system for this repo, minimal, earth tones", "audit the UI at localhost:3000 on /, /pricing and /docs", or "run an AI-slop check".

- Generated tokens go into the Tailwind theme / CSS variables, in line with `dean-design-taste` (OKLCH, light and dark together).
- Audits cite exact `file:line` for every finding and suggest the smallest fix.
