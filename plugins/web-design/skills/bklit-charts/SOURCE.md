# Source

- Tool: https://github.com/bklit/bklit-ui (uixmat; MIT for the chart components and registry; Bklit Studio is proprietary)
- This skill: Dean (original), written with Claude. No component code copied. Bklit's own agent skills (bklit-ui, bklit-ui-design, bklit-ui-migrate) are linked, not vendored, so they stay current. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at b4d5664 (LICENSE, README, packages/ui/package.json, installation and skills docs).

## Notes

- Verdict: the go-to chart library for Dean's dashboards and stats sections. It's shadcn-native, Tailwind-themed and polished, and free (MIT).
- Good at: 18+ chart types plus utilities (brush, markers, reference lines); composable API; animated, good-looking defaults; Studio to tune and export code; official agent skills including a Recharts migration; Vercel OSS program member.
- Weak at / risks:
  - a young project, so the API may change
  - visx-based, which means a few dependencies per chart
  - Studio itself is proprietary
  - no explicit license on the skills docs page (the repo is MIT)
- Alternatives:
  - shadcn charts (Recharts-based, simpler)
  - Tremor
  - Recharts / visx / ECharts directly
  - Observable Plot (data-heavy work)
