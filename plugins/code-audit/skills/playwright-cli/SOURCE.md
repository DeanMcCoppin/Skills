# Source

- Tool: https://github.com/microsoft/playwright-cli (Microsoft; Apache-2.0; npm `@playwright/cli`)
- This skill: Dean (original), written with Claude. The upstream skill (`skills/playwright-cli/` plus references) wasn't vendored; `playwright-cli install --skills` installs the version matching the CLI. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit b1a5903 (v0.1.22): README (install, sessions, dashboard, full command list, attach), skill file list. No telemetry or download-and-execute found in the README; the upstream skill's reference files were listed, not read line by line.
- No flags. Risky-by-nature features noted in the skill: persistent profiles and `state-save` (credentials on disk), `attach --cdp`/`--extension` (the real browser), `eval`/`run-code`. The README's install is `npm install -g @playwright/cli@latest` (global, unpinned); the skill installs per project, pinned.

## Notes

- Verdict: the default way to give Claude a browser in Dean's projects. Official, small, cheaper on tokens than the MCP, with sessions and a dashboard to watch agents' browsers.
- Good at: snapshot + refs workflow, screenshots, console/network inspection, tracing and video, request mocking, generating Playwright test code from a session.
- Weak at: young (0.1.x, commands may change), exploratory multi-step reasoning over page structure is still better in the MCP per its own README.
- Alternatives: Playwright MCP (persistent state, richer introspection), Chrome DevTools MCP, Claude in Chrome for Dean's own logged-in browser.
- Filed in code-audit next to `browser-qa` and `e2e-testing`, which it powers.
