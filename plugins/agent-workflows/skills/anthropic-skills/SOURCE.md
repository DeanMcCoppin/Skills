# Source

- Tool: https://github.com/anthropics/skills (Anthropic). Marketplace `anthropic-agent-skills` with plugins `document-skills`, `example-skills`, `claude-api`, `academy-guide`, `discernment-nudge`.
- Licenses (per skill `LICENSE.txt`): Apache-2.0 for the example skills; **proprietary, source-available** for `docx`, `xlsx`, `pptx`, `pdf` ("© 2025 Anthropic, PBC. All rights reserved"). Nothing vendored here: the proprietary ones can't be copied, and the Apache ones are better updated upstream.
- This skill: Dean (original pointer), written with Claude. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit dbd4588: README, marketplace manifest, every skill's frontmatter and license header, the descriptions of discernment-nudge and academy-guide. Skill bodies weren't all read line by line (official Anthropic source).
- No flags. Note: `academy-guide` and `discernment-nudge` are written to trigger very broadly ("stop and check this skill before finishing any reply…"); that's by design, but it adds content to many replies.

## Notes

- Verdict: install `document-skills` wherever a project produces Office files or PDFs, and `skill-creator` while working on this repo. Most of the rest overlap Dean's skills or are niche.
- Correction recorded: Anthropic's `frontend-design` in this repo is Apache-2.0 (the copy inside the claude-code repo is "All rights reserved"); see `design-skill-packs`.
- Alternatives: claude.ai's built-in file creation (same document skills), `anthropic-skills:*` already available in Claude cloud sessions.
