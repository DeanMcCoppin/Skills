# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/react-performance (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: ECC maintainers, adapted from Vercel Labs react-best-practices (MIT, Vercel Engineering)
- License: MIT (ECC) / MIT (Vercel upstream)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: split into a short SKILL.md (priority table and method) and references/rules.md (full catalogue, kept nearly verbatim); updated React Compiler status (stable) and removed FID (retired); removed links to ECC-only skills, agents and commands; kept Vercel attribution.
- Upstream: https://github.com/vercel-labs/agent-skills/tree/main/skills/react-best-practices (MIT, Vercel).

## Notes

- Verdict: the best single React/Next perf reference here; use the priority order and measure first.
- Good at: 70+ rules by impact with examples; Web Vitals mapping; Server Action auth reminder.
- Weak at / risks: some numbers are rough ("200-800ms"); manual memo rules matter less with React Compiler.
- Alternatives: Vercel upstream skill (vercel-labs/agent-skills) for the original; Next.js docs; Lighthouse/Web Vitals.
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
