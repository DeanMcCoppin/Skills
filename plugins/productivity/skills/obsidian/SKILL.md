---
name: obsidian
description: "Work with Dean's Obsidian vault from Claude Code using kepano's official-adjacent obsidian-skills plugin (Obsidian-flavored Markdown with wikilinks, embeds, callouts and properties; Bases; JSON Canvas; the Obsidian CLI) - install it, point Claude at the vault, and keep edits safe. Use when Dean wants Claude to write, organize or query Obsidian notes, build canvases or Bases, or mentions Obsidian or obsidian-skills."
metadata:
  pricing: free
  cost: "Skills free (MIT). Obsidian is free for personal and commercial use; Sync and Publish are optional paid add-ons."
  tags: [notes, obsidian, markdown, knowledge-management, pkm]
---

# Obsidian

Install the upstream skills (maintained by kepano, Obsidian's CEO) instead of copying them:

```
/plugin marketplace add kepano/obsidian-skills
/plugin install obsidian@obsidian-skills
```

They cover `obsidian-markdown` (wikilinks `[[Note]]`, embeds `![[…]]`, callouts, frontmatter properties, tags), `obsidian-bases` (`.base` database views), `json-canvas` (`.canvas` files), `obsidian-cli`, `defuddle` (clean Markdown from a web page) and `knap` (Markdown notes from templates plus JSON/CSV data). Defuddle and Knap are separate CLIs; install them only if needed, pinned.

## Working in a vault

- Open Claude Code **in the vault folder** (or `--add-dir` it) only for note work; don't give a client project session access to the vault.
- Ask before mass edits (renames, moving folders, rewriting frontmatter): links break across the vault. Prefer Obsidian's own rename (or the CLI) so links update.
- Use the vault's existing conventions (folders, tag style, property names) before inventing new ones. Read a few notes first.
- Keep `.obsidian/` (settings, plugins) out of Claude's edits unless Dean asks.
- Back up or commit the vault (git) before a large reorganization.
