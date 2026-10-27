# Source

- Tool: https://github.com/safishamsi/graphify (PyPI `graphifyy`)
- Author: Safi Shamsi and contributors
- License: dual MIT (LICENSE-MIT) / Apache-2.0 (LICENSE)
- This skill: Dean (original), written with Claude. Their own skill files (per-agent `graphify/skills/*`) weren't vendored, because `graphify install --project` generates them for the installed version. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at commit dac0634 (v0.9.96). Read the README, SECURITY.md and the Claude skill's hooks reference. Searched the Python package (~2,800-line install.py, cli, llm, ingest, security, querylog) for network calls, telemetry and config writes. Not a full audit of all ~1,100 files.
- Flag raised: the default `graphify install` writes to global `~/.claude/skills`, `~/.claude/CLAUDE.md` and adds PreToolUse hooks (`hook-guard search`/`read`). The skill mandates `--project` scope instead.

## Notes

- Verdict: a strong fit for token-efficiency on large or unfamiliar codebases. Local, deterministic code graphs with honest EXTRACTED/INFERRED tagging. Install per project only.
- Good at:
  - tree-sitter AST across many languages, with no LLM for code
  - query, explain and path commands
  - graph.html visualization and GRAPH_REPORT.md for onboarding
  - an incremental post-commit rebuild
  - MCP server option
  - support for 20+ assistants
  - very active (frequent releases)
- Weak at / risks:
  - global install and hooks by default
  - semantic extraction of docs and media sends content to a model
  - stale graphs can mislead
  - the "80% fewer tokens" headline is unverified marketing (and upsells Graphify Cloud)
  - a big, fast-moving codebase (pin the version)
- Alternatives: Claude Code's own search plus subagents for exploration; SCIP/LSP-based code intelligence; Sourcegraph (hosted).
