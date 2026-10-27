# Source

- Source: https://github.com/forrestchang/andrej-karpathy-skills (skill `skills/karpathy-guidelines`, plus CLAUDE.md and EXAMPLES.md)
- Author: forrestchang (Jiayuan); based on Andrej Karpathy's public post on LLM coding pitfalls
- License: MIT, as declared in the README, plugin.json and SKILL.md frontmatter. The repo has **no LICENSE file**, so there's no copyright line to carry; credit is given here.
- Imported: 2026-10-27 at commit 2c60614. Every file was read in full (README, SKILL.md, CLAUDE.md, CURSOR.md, EXAMPLES.md, manifests, Cursor rule); nothing was executed.
- Changes:
  - description rewritten for triggering
  - added metadata (pricing, tags)
  - linked EXAMPLES.md as references/examples.md (unchanged)
  - appended the "working if" line from their CLAUDE.md and links to related skills in this repo
  - not imported: their Cursor rule, CURSOR.md, Chinese README, and the README's promotion of the author's Multica project
- Category: code-audit, because it governs how code changes are made and reviewed ("every changed line should trace to the request"). Its primary purpose is change quality, not token savings, though it reduces rework too.

## Merged: Ponytail (2026-10-27)

- Source: https://github.com/DietrichGebert/ponytail (Dietrich Gebert; MIT, Copyright (c) 2026 Dietrich Gebert). Reviewed at commit 09c434a: skills/ponytail/SKILL.md, hooks (activate, mode tracker, subagent, map, config, runtime), manifests, README claims.
- Merged instead of imported, because its core job is the same as section 2 ("Simplicity First"). Taken, rephrased: the "first option that fully works" ladder, "lazy about the solution, never about the change", the never-cut list, and the `shortcut:` comment form.
- Not taken: the plugin's always-on mode and levels, `/ponytail-audit`, `-review`, `-debt`, `-gain`.
- Flags (why not installed as a plugin): its SessionStart, SubagentStart and UserPromptSubmit hooks inject the ruleset into every session and subagent, write flag files into `~/.claude` (`$CLAUDE_CONFIG_DIR`), run `git ls-files` to build a repo map, and nudge Claude to edit the global `statusLine` in `~/.claude/settings.json`. No network calls found. Fine if Dean wants its audit/review commands: install per project and approve the hooks in `/hooks`.
- Claims: README says ~54% less code on its own 39-task benchmark; an independent JetBrains test reported ~15%. Third-party star counts (76k to 128k) unverified.

## Notes

- Verdict: short, high-value, always-on coding discipline. Enable it in every coding project; it costs almost no context.
- Good at: curbing over-engineering, drive-by refactors and silent assumptions; forcing verifiable success criteria; concrete before/after examples.
- Weak at / risks:
  - biases toward asking questions, which can slow trivial tasks (the skill says to use judgment)
  - Claude Code's own defaults already push some of this, so expect overlap rather than conflict
  - the "duplicate scores" test-first example in examples.md wouldn't actually detect the bug it describes (Python's sort is stable), so treat it as an illustration of the process, not a correct test
- Ponytail is a heavier take on the same idea (see above).
- Alternatives: putting the same four rules directly in a project's CLAUDE.md (their repo offers that form); `production-audit` and `security-review` for what to check rather than how to change code.
