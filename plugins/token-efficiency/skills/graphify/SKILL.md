---
name: graphify
description: "Map a codebase (plus docs, PDFs, images) into a queryable knowledge graph with graphify, so Claude can explain concepts, trace paths between symbols and find relevant code from graph.json instead of grepping and reading many files - code parsing is local and deterministic (tree-sitter), installed per project. Use when Dean works in a large or unfamiliar codebase, onboards to a client's repo, wants to cut context or token use on codebase questions, or mentions graphify or a code knowledge graph."
metadata:
  pricing: free
  cost: "Free (MIT or Apache-2.0); code mapping is fully local. Docs/PDF/image extraction uses the session's model or a configured API key. Graphify Cloud is a separate paid product."
  tags: [codebase-map, knowledge-graph, context, tokens, onboarding]
---

# graphify

[safishamsi/graphify](https://github.com/safishamsi/graphify) (dual MIT / Apache-2.0, PyPI package **`graphifyy`**) builds `graphify-out/graph.json`, a clickable `graph.html` and a `GRAPH_REPORT.md` (key concepts, surprising links, suggested questions). Every edge is tagged `EXTRACTED` (read from source) or `INFERRED`.

## Install: per project, never global

```bash
uv tool install graphifyy==0.9.96      # pin; update deliberately
cd <project>
graphify install --project             # project-scoped skill (commit it if the team uses it)
```

- **Don't run the bare `graphify install`.** It writes to Dean's **global** `~/.claude/skills`, `~/.claude/CLAUDE.md` and adds **PreToolUse hooks** that intercept every search and read in all projects. Use project scope only.
- `graphify claude install --project` adds a `## graphify` section to the project's CLAUDE.md ("check the graph first"). That's optional, and only for big repos where it pays off.
- The post-commit hook (`graphify hook install`) rebuilds the graph after each commit. It's convenient for active repos; it appends to any existing hook.
- Add `graphify-out/` to `.gitignore` unless the team wants the graph committed.

## Use

```
/graphify .                         # build the graph (code: local AST, no LLM)
graphify query "how does checkout create an order?"
graphify explain "PaymentService"
graphify path "CheckoutPage" "stripeWebhook"
```

- Answer codebase questions from the graph first, then read only the few files it points to. That's where the token savings come from.
- Trust `EXTRACTED` edges; verify `INFERRED` ones in the source before relying on them for a change.
- Rebuild after big changes (`/graphify --update`, or the commit hook). A stale graph misleads.

## Data and privacy

- Code extraction never leaves the machine. **Docs, PDFs, images and video** are sent to the assistant's model or a configured API key for semantic extraction, so skip those folders on confidential client repos, or keep them on a local model (`ollama`).
- `graphify ingest` fetches URLs explicitly; the HTTP MCP mode is an opt-in network listener (keep it on localhost). Query logging is off unless enabled.
- The "cut token spend by 80%" headline is the project's own claim. Measure it on a real repo.

Pairs with `strategic-compact` (keep sessions lean) and `karpathy-guidelines` (surgical changes once you've found the code).
