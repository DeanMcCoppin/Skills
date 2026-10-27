# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/e2e-testing (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: ECC maintainers
- License: MIT (ECC repository license)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: added Principles (user-facing locators, web-first assertions, storageState auth, axe checks); replaced networkidle waits (discouraged by Playwright) with response/locator waits; replaced Chromium-only browser.startTracing with Playwright trace config and context.tracing; fixed the invalid `videosPath` option; Node 22 in CI; removed the Web3 wallet and trading sections.

## Notes

- Verdict: good Playwright starter for client sites; set it up for launch-critical flows.
- Good at: POM structure, config, CI workflow, flaky-test tactics, report template.
- Weak at / risks: POM can be overkill for small sites; keep tests close to user flows.
- Alternatives: Playwright docs best practices; Cypress (not preferred).
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
