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

## Notes

- Verdict: short, high-value, always-on coding discipline. Enable it in every coding project; it costs almost no context.
- Good at: curbing over-engineering, drive-by refactors and silent assumptions; forcing verifiable success criteria; concrete before/after examples.
- Weak at / risks:
  - biases toward asking questions, which can slow trivial tasks (the skill says to use judgment)
  - Claude Code's own defaults already push some of this, so expect overlap rather than conflict
  - the "duplicate scores" test-first example in examples.md wouldn't actually detect the bug it describes (Python's sort is stable), so treat it as an illustration of the process, not a correct test
- Alternatives: putting the same four rules directly in a project's CLAUDE.md (their repo offers that form); `production-audit` and `security-review` for what to check rather than how to change code.
