# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/mcp-dependency-review (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: ECC maintainers
- License: MIT (ECC repository license)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: description rewritten; replaced an ECC-specific package example with a neutral one; removed links to ECC-only skills.

## Notes

- Verdict: excellent and strictly static; run it whenever an .mcp.json changes (including REA's per-project setup).
- Good at: clear SAFE/MEDIUM/HIGH/REVIEW rules for npm, Docker and Python selectors; never executes servers; honest boundaries.
- Weak at / risks: covers version drift only, not whether a server is trustworthy.
- Alternatives: Socket.dev or npm audit for package risk; the add-skill review checklist.
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
