# Source

- Source: https://github.com/JuliusBrussee/caveman, file `skills/caveman/SKILL.md`
- Author: Julius Brussee. License: Apache-2.0 (whole repo since 3.0.0; copy in `LICENSE.txt`). Copyright 2026 Julius Brussee. "Caveman" and the rock logo are trademarks of Julius Brussee; used here only to name the source.
- Imported: 2026-10-27 at commit 9b68f7e (v4.0.x). Read in full: the skill (89 lines), README (install, six parts, privacy, license), LICENSING.md, NOTICE, INSTALL.md privacy notes. Nothing executed.
- Changes (Apache-2.0 §4b, modified file):
  - new frontmatter: description for triggering, metadata
  - on request only (upstream: "Unsure if still on? It is")
  - removed the `/caveman ultra|wenyan|status` paragraph (needs their hooks and other skills)
  - added the closing line pointing to `token-budget-advisor`
- Flags raised (why only the skill was imported):
  - The recommended install `npx @caveman-ai/cli@latest` "finds your agents and your logins" and sets up a local **proxy** that all agent traffic goes through, plus Read-less, Auto, Blocks, Browse and other parts, all on after install.
  - **CLI telemetry on by default**: commands, token counts, install ID, OS and **IP address** (`caveman telemetry off`).
  - **Auto** (opt-in, needs login): sends your latest asks, attached context (CLAUDE.md, memory, @-files) and reply tails to Caveman Cloud; requests routed to Caveman Cloud models pass through it whole.
  - Alternate install `curl … install.sh | bash` (download-and-execute).
  - `/caveman-compress` sends the file to the model provider (not imported).

## Notes

- Verdict: the voice is well designed (answer first, meaning never dropped, verbatim payload, clear exceptions) and worth having on request. Savings are modest on modern models: their own numbers show `/caveman` only ~3% under a plain "answer concisely" at the median (ultracave ~35%), and JetBrains measured 8.5% fewer output tokens with no quality loss. The full CLI and proxy aren't worth the privacy trade for Dean.
- Good at: shorter chat replies in long sessions, no damage to code or commands, research-backed rules (ASD-STE100).
- Weak at: costs ~1,100 input tokens per session for a few percent output savings; terse prose can hide nuance.
- Alternatives: `token-budget-advisor` (one-off length control), `strategic-compact`, Claude Code's output style settings.
