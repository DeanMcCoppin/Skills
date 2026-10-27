# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/browser-qa (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: ECC maintainers
- License: MIT (ECC repository license)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: fixed the MCP tool names (`mChild__…` typo; Browserbase is not Playwright); removed the /canary-watch reference; links to e2e-testing and accessibility; description rewritten.

## Notes

- Verdict: great post-deploy smoke-and-verdict routine; safe by default (read-only, test credentials, redaction).
- Good at: smoke, interactions, 3-breakpoint visual checks with honest INCONCLUSIVE when there is no baseline, axe with caveats.
- Weak at / risks: needs a browser tool in the session; Web Vitals from one run are lab numbers, not field data.
- Alternatives: Playwright visual comparisons in CI; Lighthouse CI.
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
