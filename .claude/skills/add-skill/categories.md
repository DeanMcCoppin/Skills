# Categories

Each category is one plugin in this marketplace, so Dean can enable categories separately per project. Don't rename existing ones: the plugin name is the install ID (`<plugin>@dean-skills`) used in every project's settings.

| Category | Plugin folder | Put it here when the skill's main job is… | Not here |
| --- | --- | --- | --- |
| Token optimisation | `plugins/token-efficiency` | Using fewer tokens or less context: concise output styles, compaction and summarizing, context and memory management, subagent delegation to save context, choosing cheaper models or effort, batching or caching work | General productivity or writing style that isn't about cost or context |
| Code auditing | `plugins/code-audit` | Judging existing code: code review, security review, performance profiling, accessibility audits, dead code, dependency and license checks, test coverage gaps, lint-style rules | Writing new features; design-quality critiques of a UI (→ website design) |
| Website design | `plugins/web-design` | Making web UIs look and feel good: UI/UX, typography, color, layout, design systems, Tailwind, Framer Motion and animation, interactive maps (Mapbox, Google Maps), landing pages and marketing sites | Backend, APIs, auth, databases; a11y *audits* (→ code auditing) |
| Media generation | `plugins/media-generation` | Generating images, video or audio with AI models, and media tools around them (downloading, converting, trimming): generation tools and studios, model selection, prompting for realism, consistency across shots, exporting media for sites | Building the website that shows the media (→ website design) |
| SEO | `plugins/seo` | Getting found in search: keyword and competitor research, SEO audits, backlinks, rank tracking, local SEO, AI-answer visibility, Search Console, SEO data tools, privacy-friendly web analytics | On-page code quality or performance audits (→ code auditing); visual page design (→ website design) |
| Knowledge | `plugins/knowledge` | Making documents answerable: knowledge bases, RAG, document Q&A, knowledge graphs, wikis built from docs, docs chatbots and widgets, feeding docs to agents over MCP | Writing or editing the docs themselves; general context-saving tricks (→ token optimisation) |
| Productivity | `plugins/productivity` | Speeding up Dean's own day-to-day work: dictation and voice input, meeting transcription and notes, project and task management, scheduling and booking, screen recording, notes and wikis, password and secrets management, launchers, clipboard and window tools, personal automation | Generating media (→ media generation); context or token savings (→ token optimisation); team knowledge bases (→ knowledge) |
| Customer support | `plugins/customer-support` | Talking to customers of Dean's or client sites: live chat widgets, shared support inboxes (email, WhatsApp, social), help centers and FAQs, helpdesk and ticketing | AI answers from documents (→ knowledge); scheduling (→ productivity) |
| Local AI | `plugins/local-ai` | Running AI models on Dean's own hardware: model runtimes (Ollama, LM Studio, llama.cpp), local embeddings, local OpenAI/Anthropic-compatible APIs, using local models in other tools | Tools that merely *can* use a local model as an option (file them by their main job and link here) |
| Automation | `plugins/automation` | Connecting apps and automating processes: n8n/Zapier/Make-style workflow tools, webhooks, scheduled jobs, form-to-CRM pipelines, AI workflow agents | One-off scripts for Dean's own desktop (→ productivity) |

## Choosing between two

Pick the category of the skill's **output**:
- A skill that reviews a UI and outputs a list of problems is **code auditing**. One that outputs a redesign is **website design**.
- A skill that makes reviews cheaper by delegating to subagents is **code auditing** if the point is the review, **token optimisation** if the point is the savings.

Say which you picked and why in the report.

## Fits none

Don't force it. Tell Dean, and suggest a new category if the skill is useful and others like it are likely (for example `backend`, `devops`, `writing`, `data`). Only create one after Dean says yes.

## Adding a new category

When Dean approves a new category `<name>` (kebab-case, not starting with `claude-` or `anthropic-`):

1. Create `plugins/<name>/.claude-plugin/plugin.json`, copying an existing one: same `author` and `repository`, `version` `0.1.0`, plus a new `displayName`, `description` and `keywords`.
2. Create `plugins/<name>/skills/` and place the skill there.
3. Add an entry to `.claude-plugin/marketplace.json`: `name`, `"source": "./plugins/<name>"`, `description`, `category`.
4. Add `"<name>@dean-skills": true` to `templates/project-settings.json`.
5. Add a row to the table above, and to the plugin tables in `README.md` and `CLAUDE.md`.
6. Run `claude plugin validate .`.
