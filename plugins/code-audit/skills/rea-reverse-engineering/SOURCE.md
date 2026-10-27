# Source

- Tool: https://github.com/morluto/rea (npm `rea-agents`; MIT for REA-authored code, third-party material under its own licenses)
- This skill: Dean (original), written with Claude. No code or instructions copied from REA's own skills or AGENTS.md. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at v6.8.0: README, DISCLAIMER.md, install.sh, package.json (only a `prepare` lifecycle script, which doesn't run on registry installs), server.json. REA's own `.agents/skills` weren't imported. The source code wasn't audited.
- Flags raised at review (Dean approved adding it with guardrails):
  1. Implausible popularity: 347k stars in the promo, 395k stars and 99k forks on the page, "300,000" in its own star history. That would rank it among the very top repos on GitHub, so treat the popularity as meaningless (possibly purchased).
  2. `npx rea-agents setup` writes to the global config of every installed agent and installs instructions, so the skill uses a manual per-project `claude mcp add` instead.
  3. Runtime capture runs targets with the user's permissions.
  4. Dual-use: legal limits on reverse engineering vary by license and country.

## Notes

- Verdict: a capable, well-engineered tool for auditing and debugging what software really does. Use it on Dean's own apps, dependencies and authorized targets, with the guardrails in SKILL.md. Ignore the star count.
- Why it still looks engineered seriously: ~6k commits, tests and mutation testing (stryker), a careful installer (https only, pinned versions, no download-and-execute of extra code), a security policy, a clear responsible-use disclaimer, local analysis, no API keys.
- Good at:
  - one MCP for ~40 target types (Electron/JS, native via Ghidra/Hopper/IDA, .NET, APK, web, pcap, firmware)
  - evidence-backed findings
  - turning recorded web sessions into tools for testing
- Weak at / risks:
  - heavy optional toolchain, some of it commercial (IDA, Hopper, JEB)
  - powerful runtime features (terminal, browser automation, running targets)
  - global setup rewrites agent configs
  - the popularity signals look manipulated
  - the legal grey zone if pointed at third-party software
- Alternatives:
  - Ghidra directly (free, manual)
  - browser DevTools and HAR analysis (for web)
  - `npm pack` + reading the source (for packages)
  - Socket.dev / npm audit (for dependency risk)
- Review: re-check on version bumps (runtime/network features, setup behavior). Re-evaluate if the star or fork numbers keep jumping.
