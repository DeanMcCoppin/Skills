---
name: repomix
description: "Pack a repository (or part of one) into a single AI-friendly file with Repomix - token counts per file, tree-sitter --compress to keep only signatures, Secretlint scanning, remote repos - to hand a codebase to another model or chat, review an unfamiliar repo in one shot, or share context with a non-agent tool. Use when Dean wants to paste a whole repo into Claude.ai, ChatGPT or Gemini, needs a token count for a codebase, wants a compressed snapshot of a library, or mentions Repomix."
metadata:
  pricing: free
  cost: "Free (MIT). Runs locally; the repomix.com web version is free too."
  tags: [context, codebase-snapshot, tokens, packing, cli]
---

# Repomix

[yamadashy/repomix](https://github.com/yamadashy/repomix) (MIT) writes the repo as one XML/Markdown/plain file with a directory tree, file contents and token counts.

## When to use it (and when not)

- ✅ Handing a codebase to a chat model without repo access (Claude.ai project, Gemini's long context), a second-opinion review, or comparing a library's source.
- ✅ Getting token counts: `--token-count-tree` shows which folders blow up context.
- ❌ Inside Claude Code on the same repo: it's usually worse than letting Claude search and read files (or `graphify` on big repos). Packing everything into context is the opposite of saving tokens.

## Use (pinned)

```bash
npx repomix@<pinned-version> --style markdown -o repo.md                 # whole repo
npx repomix@<pinned-version> --include "src/**,package.json" --compress  # signatures only, much smaller
npx repomix@<pinned-version> --remote vercel/next.js --include "packages/next/src/server/**" --compress
npx repomix@<pinned-version> --token-count-tree
```

- `--compress` uses tree-sitter to keep signatures and structure and drop function bodies (often ~70% smaller).
- It respects `.gitignore` plus `repomix.config.json` / `.repomixignore`. Exclude `dist`, lockfiles, fixtures and assets.

## Safety

- Secretlint runs by default and skips files that look like they contain secrets. **Don't disable it** (`--no-security-check`), and still check the output before pasting it anywhere external. `.env` files must never be in the pack.
- Client code: only paste packed client repos into services covered by Dean's agreement with that client. Add `repo.md` (or the output name) to `.gitignore`.
- `--remote` clones the repo to a temp folder; packing doesn't execute its code.
