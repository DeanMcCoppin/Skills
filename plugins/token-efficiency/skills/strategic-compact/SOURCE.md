# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/strategic-compact (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: ECC maintainers
- License: MIT (ECC repository license)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: kept the decision guidance only: removed the ECC hook (suggest-compact.js is not included and writes to ~/.claude/settings.json), its env vars, the promotional "95% token reduction" tool claims and the X link; replaced the trigger-table section with practical baseline-context tips.

## Notes

- Verdict: useful habits for long sessions; no automation.
- Good at: a phase-transition table for when to compact; what survives compaction; "write the plan to a file first".
- Weak at / risks: Claude can only suggest; Dean runs /compact.
- Alternatives: Claude Code's built-in auto-compact and /context; subagents to keep the main context small.
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
