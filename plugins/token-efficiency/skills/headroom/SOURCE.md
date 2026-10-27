# Source

- Tool: https://github.com/chopratejas/headroom (Tejas Chopra / Headroom Labs; Apache-2.0; PyPI `headroom-ai`, docs at docs.headroomlabs.ai)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit 17d38e5: README (install, wrap, proxy, TLS, learn, telemetry, Enterprise table). The Python/Rust code (~large) wasn't audited.
- Flags raised:
  - Telemetry beacon on by default (compression ratios, counters, provider/model IDs, OS); no prompts or code per its docs. Off with `HEADROOM_TELEMETRY=off` / `DO_NOT_TRACK=1` / `HEADROOM_OFFLINE=1`.
  - It is a proxy for all agent traffic (by design); `wrap` also installs Serena MCP and writes `~/.claude.json`.
  - `headroom learn` edits CLAUDE.local.md / CLAUDE.md automatically.
  - README links an Enterprise promo with UTM tracking.

## Notes

- Verdict: promising and well documented, but a big moving part between Dean and Claude. Try it on a log- or data-heavy side project, measure with its dashboard, keep it only if savings are real. Not a default.
- Good at: reversible compression (originals retrievable), JSON/log/search output, MCP mode, many agents supported, a dashboard.
- Weak at / risks: lossy summaries can mislead; another process holding all traffic; telemetry default; heavy install (Python 3.13, ML models); savings on plain coding much smaller than the headline.
- Alternatives: `strategic-compact`, `graphify`, `repomix --compress`, `caveman` (output side), Claude Code's own compaction. Comparisons online (caveman vs ponytail vs rtk vs pxpipe vs headroom) treat these as complementary: output style vs input compression.
