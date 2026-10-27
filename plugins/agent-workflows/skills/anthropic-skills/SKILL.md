---
name: anthropic-skills
description: "Pick and install Anthropic's official skills (anthropics/skills marketplace: document skills for Word, Excel, PowerPoint, PDF; skill-creator; mcp-builder; webapp-testing; frontend-design; theme-factory; claude-api and others) per project, and know which ones Dean's own skills already cover. Use when Dean asks about Anthropic's or the official Claude skills, needs to create or edit .docx/.xlsx/.pptx/.pdf files in Claude Code, wants to write or test a new skill, build an MCP server, or asks which official skills to install."
metadata:
  pricing: free
  cost: "Free to use. Most example skills Apache-2.0; the document skills (docx, xlsx, pptx, pdf) are source-available, proprietary Anthropic license (use, don't copy)."
  tags: [anthropic, official, skills, documents, skill-creator, mcp]
---

# Anthropic's skills

```
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

Install per project (record in the project's `.claude/settings.json`), and only the plugins that project needs. On claude.ai, Cowork and the desktop app, the document skills already ship built in.

| Skill | Use it for | vs. this repo |
| --- | --- | --- |
| `docx`, `xlsx`, `pptx`, `pdf` (**document-skills**) | Creating and editing Office files and PDFs from Claude Code: client proposals, reports, invoices, decks | Nothing here covers it. Install when a project produces documents |
| `skill-creator` | Writing a new skill, testing its triggering with evals, tightening descriptions | Use it alongside this repo's add-skill flow for Dean's original skills; the add-skill review still applies |
| `mcp-builder` | Building an MCP server for a client API or Dean's own tools | Nothing here covers it |
| `webapp-testing` | Python Playwright scripts against a local app | `playwright-cli` is the default; use this only for scripted Python checks |
| `frontend-design` | "Avoid the generic AI look" guidance | Covered by `dean-design-taste` and `design-skill-packs`; skip |
| `theme-factory` | 10 preset themes for artifacts, slides and docs | Fine for internal docs; client sites use `design-md` / `dean-design-taste` |
| `claude-api` | Building apps on the Claude API | Install in projects that call the Claude API |
| `web-artifacts-builder`, `canvas-design`, `algorithmic-art`, `slack-gif-creator` | Artifacts, posters, generative art, GIFs | Occasional; enable only when needed |
| `brand-guidelines`, `internal-comms` | Anthropic's own brand and comms formats | Not for Dean; examples of the pattern only |
| `academy-guide`, `discernment-nudge` | Points to Claude Academy courses; appends "check this" follow-up questions to advice | Optional; both trigger broadly and add text to many replies |

The `example-skills` plugin installs all of its skills at once, so enabling it is mostly about `skill-creator` and `mcp-builder`. Turn it off in projects where the extra skills add noise.
