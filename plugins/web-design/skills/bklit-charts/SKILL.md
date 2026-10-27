---
name: bklit-charts
description: Add polished, animated charts to React/Next.js apps with Bklit UI, a free MIT shadcn registry of composable charts (area, bar, line, pie, ring, radar, gauge, funnel, heatmap, sankey, sparkline, candlestick, choropleth and more) built on visx. Use when Dean needs charts, dashboards, analytics or stats sections, KPI sparklines, or wants to replace Recharts or shadcn's ChartContainer, or mentions Bklit.
---

# Bklit charts

[Bklit UI](https://bklit.com) ([bklit/bklit-ui](https://github.com/bklit/bklit-ui), MIT) is a shadcn registry: components are copied into the project (`components/charts/`), not installed as a black-box package. Bklit Studio (the visual playground at bklit.com/studio) is proprietary but free to use for exporting code.

## Install

Requires shadcn/ui in the project (`npx shadcn@latest init`; Tailwind v4 projects work).

```bash
npx shadcn@latest add @bklit/bar-chart      # or area-chart, line-chart, pie-chart, ring-chart, radar-chart…
```

New shadcn projects resolve `@bklit` automatically. In an older project, add this to `components.json`:

```json
{ "registries": { "@bklit": "https://ui.bklit.com/r/{name}.json" } }
```

Charts: area, bar, candlestick, choropleth, composed, funnel, gauge, heatmap, line, profit/loss line, live line, pie, radar, ring, scatter, sankey, sparkline, sunburst. Utilities: legend, grid, tooltip, axis, brush, markers, reference area, trend/projection lines.

**Official agent skills** (keep them current from upstream rather than copying them here):

```bash
npx skills add bklit/bklit-ui --skill bklit-ui          # install, compose, theme, animate
npx skills add bklit/bklit-ui --skill bklit-ui-design   # patterns, gradients, loading states, matching the app theme
npx skills add bklit/bklit-ui --skill bklit-ui-migrate  # from Recharts / shadcn ChartContainer / TanStack
```

Install them per project when doing real chart work.

## Defaults for Dean

- Charts are composable: build from parts (`BarChart`, `Bar`, `BarXAxis`, `Grid`, `ChartTooltip`…) and add only what the data story needs. Default to a grid, a tooltip and one axis; skip legends when there's a single series.
- Theme through the project's CSS variables (`dean-design-taste` tokens), not per-chart hex values. Check both light and dark mode.
- One accent for the series that matters, neutrals for the rest. No rainbow palettes.
- Use **Studio** to tune a chart visually, then export the code into the project.
- Charts are client components: keep data fetching in Server Components and pass plain data down.
- Accessibility: a visible title or `aria-label` describing the takeaway, a data table or summary text for screen readers on key charts, and contrast that works without color alone.
- Performance: sparklines for small KPIs; lazy-load heavy charts below the fold.
