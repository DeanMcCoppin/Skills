# Skills

My personal Claude Code skills, packaged as a plugin marketplace called **`dean-skills`**. Skills are grouped into plugins so each category can be turned on per project.

| Plugin | What's in it |
| --- | --- |
| `token-efficiency` | Context management, concise output, compaction, cheaper workflows |
| `code-audit` | Reviews, security, performance, accessibility, dead code, dependency checks |
| `web-design` | UI/UX, typography, layout, Tailwind, Framer Motion, maps, landing pages |
| `media-generation` | AI image, video and voice generation (Open Higgsfield, VoiceStudio, model choice, prompting) |
| `seo` | SEO and analytics: keyword and competitor research, technical SEO, rank tracking, privacy-friendly analytics (OpenSEO, Plausible) |
| `knowledge` | AI knowledge bases: RAG Q&A over documents, site chatbots, MCP access to docs, current library docs (WeKnora, Context7) |
| `productivity` | Tools for your own workflow: voice dictation, meeting notes, project management, scheduling, screen recording (OpenWhispr, OpenProject, Cal.com, Cap) |
| `customer-support` | Live chat widgets, shared support inboxes, help centers for your and client sites (Chatwoot) |
| `local-ai` | Run AI models on your own machine: local LLMs, embeddings and APIs (Ollama) |
| `automation` | Workflow automation and integrations: n8n (+ n8n-MCP), webhooks, scheduled jobs |
| `agent-workflows` | How Claude Code works: workflow frameworks (Superpowers vs GSD), memory across sessions (claude-mem) |

## Skills catalog

One line per skill. The full verdict (strengths, weaknesses, alternatives) is in each skill's `SOURCE.md`.

**Cost legend** (details in each skill's `metadata.cost` and `SOURCE.md`; prices as of 2026-10-27):
🟢 **Free**: no cost · 🟢 **Free (self-host)**: free software, you run the server · 🟡 **Freemium**: useful free tier, paid plan for some features or commercial use · 🟠 **Pay-per-use**: the tool is free but usage (API calls, generations, data) is billed · 🔴 **Paid**: needs a paid plan to use at all

| Skill | Plugin | Cost | Use it when | Verdict | Tags |
| --- | --- | --- | --- | --- | --- |
| [`strategic-compact`](plugins/token-efficiency/skills/strategic-compact/SKILL.md) | token-efficiency | 🟢 Free | Long sessions: when to `/compact` and what to save first; keeping baseline context small | Useful habits, no hooks (from ECC, stripped of its global hook) | `context` `compaction` `long-sessions` |
| [`token-budget-advisor`](plugins/token-efficiency/skills/token-budget-advisor/SKILL.md) | token-efficiency | 🟢 Free | Only when you ask for a short, long or "50%" answer, or for token estimates | Handy on request; estimates are rough (TBA via ECC, MIT) | `tokens` `response-length` |
| [`openspace`](plugins/token-efficiency/skills/openspace/SKILL.md) | token-efficiency | 🟠 Pay-per-use | Skill retrieval and evolution across a big library (local only) | Overlaps this repo; telemetry and traces if cloud is on; claims unverified. Try on a side project. MIT | `skills` `agents` `mcp` `skill-evolution` `retrieval` |
| [`graphify`](plugins/token-efficiency/skills/graphify/SKILL.md) | token-efficiency | 🟢 Free | Big or unfamiliar codebases: query a local code knowledge graph instead of grepping and reading | Strong; code mapping is local. Install per project only (global install adds hooks everywhere). MIT/Apache | `codebase-map` `knowledge-graph` `context` `tokens` `onboarding` |
| [`repomix`](plugins/token-efficiency/skills/repomix/SKILL.md) | token-efficiency | 🟢 Free | Packing a repo into one file for a chat model without repo access; token counts per folder | Great utility; not a token saver inside Claude Code (use search or graphify there). Keep Secretlint on. MIT | `context` `codebase-snapshot` `tokens` `packing` `cli` |
| [`karpathy-guidelines`](plugins/code-audit/skills/karpathy-guidelines/SKILL.md) | code-audit | 🟢 Free | Any coding task: ask instead of assuming, minimum code, surgical diffs, tests-first goals | Short, always-on coding discipline; enable everywhere. MIT (declared) | `coding-practices` `simplicity` `diffs` `testing` `guidelines` |
| [`rea-reverse-engineering`](plugins/code-audit/skills/rea-reverse-engineering/SKILL.md) | code-audit | 🟢 Free | Inspecting what your own apps, dependencies, SDKs or third-party scripts really do (bundles, Electron, APKs, network captures), with evidence | Capable and well built; use only on authorized targets with per-project MCP setup. Star count looks fake. MIT | `reverse-engineering` `security` `mcp` `dependencies` |
| [`security-review`](plugins/code-audit/skills/security-review/SKILL.md) | code-audit | 🟢 Free | Auth, input, secrets, uploads, payments, API routes, pre-deploy security; cloud/CI reference | Solid baseline checklist (from ECC, Solana removed, rate limiting fixed for Next.js) | `security` `auth` `nextjs` `supabase` `checklist` |
| [`production-audit`](plugins/code-audit/skills/production-audit/SKILL.md) | code-audit | 🟢 Free | "Ready to ship?" pre-launch or handover audit with score and ship/block verdict | Excellent, local-only (from ECC) | `launch` `readiness` `audit` `webhooks` |
| [`react-performance`](plugins/code-audit/skills/react-performance/SKILL.md) | code-audit | 🟢 Free | Slow React/Next.js pages, bundle size, waterfalls, re-renders, Web Vitals | Best perf reference here (Vercel rules via ECC, updated) | `react` `nextjs` `performance` `web-vitals` |
| [`accessibility`](plugins/code-audit/skills/accessibility/SKILL.md) | code-audit | 🟢 Free | WCAG 2.2 AA for React/Next.js: forms, focus, ARIA, contrast, audits | A11y baseline (from ECC, 2 skills merged, SC numbers fixed) | `a11y` `wcag` `react` `forms` |
| [`e2e-testing`](plugins/code-audit/skills/e2e-testing/SKILL.md) | code-audit | 🟢 Free | Writing Playwright tests, CI setup, flaky tests | Good starter (from ECC, outdated Playwright advice fixed) | `testing` `playwright` `ci` |
| [`browser-qa`](plugins/code-audit/skills/browser-qa/SKILL.md) | code-audit | 🟢 Free | Post-deploy check of a live or preview URL with a SHIP / DO NOT SHIP verdict | Safe-by-default QA routine (from ECC) | `qa` `post-deploy` `visual-regression` `a11y` |
| [`playwright-cli`](plugins/code-audit/skills/playwright-cli/SKILL.md) | code-audit | 🟢 Free | Claude driving a real browser: click through, screenshot, debug, generate Playwright tests | Default browser tool (Microsoft, cheaper than the MCP). Per-project pinned install; saved logins are credentials. Apache-2.0 | `browser` `playwright` `testing` `debugging` `screenshots` |
| [`mcp-dependency-review`](plugins/code-audit/skills/mcp-dependency-review/SKILL.md) | code-audit | 🟢 Free | Reviewing `.mcp.json` changes for unpinned packages, without running them | Excellent, strictly static (from ECC) | `mcp` `supply-chain` `security` |
| [`dean-design-taste`](plugins/web-design/skills/dean-design-taste/SKILL.md) | web-design | 🟢 Free | Any web UI work. Sets my default stack, look and motion rules | Baseline for every frontend; fonts and colors still TODO | `design` `nextjs` `tailwind` `house-style` |
| [`editorial-themes`](plugins/web-design/skills/editorial-themes/SKILL.md) | web-design | 🟢 Free | Building a full premium "theme" site for a business (law, agency, architect, restaurant…) in a Lexington-like editorial style | Strong for marketing sites; overkill for app UIs | `themes` `marketing-sites` `typography` `editorial` |
| [`bencho-blocks`](plugins/web-design/skills/bencho-blocks/SKILL.md) | web-design | 🟡 Freemium | Adding a tactile micro-interaction or UI sound (tilt, dock, swipe, slide-to-confirm, counters…) from Bencho | 44 free MIT blocks are excellent for signature moments; needs token mapping for Tailwind. Pro is optional | `micro-interactions` `react` `framer-motion` `ui-sounds` |
| [`component-libraries`](plugins/web-design/skills/component-libraries/SKILL.md) | web-design | 🟡 Freemium | Picking and installing animated shadcn components: Cult UI, Watermelon UI, Componentry, Aceternity UI, Skiper UI, Dotmatrix (+ Bencho, Bklit) | Cult, Watermelon and Componentry are free MIT defaults; Aceternity and Dotmatrix have custom no-redistribution licenses; Skiper's license is unpublished | `shadcn` `components` `react` `framer-motion` `ui-library` |
| [`motion`](plugins/web-design/skills/motion/SKILL.md) | web-design | 🟢 Free | Any animation in React/Next.js: tokens, springs, reduced motion, modals, stagger, page transitions, drag, SVG, loaders | Main motion reference (from ECC, 3 skills merged and corrected) | `animation` `framer-motion` `react` `nextjs` |
| [`interface-polish`](plugins/web-design/skills/interface-polish/SKILL.md) | web-design | 🟢 Free | Final polish pass when a UI feels off: radii, wrapping, tabular numbers, transitions, hit areas | Short, concrete, high value. Defers to project direction (from ECC) | `polish` `ui-details` `css` |
| [`design-system`](plugins/web-design/skills/design-system/SKILL.md) | web-design | 🟢 Free | Extracting or auditing design tokens, 10-point visual audit, AI-slop check | Good audit workflow, judgment-based (from ECC) | `design-tokens` `audit` `ai-slop` |
| [`gsap`](plugins/web-design/skills/gsap/SKILL.md) | web-design | 🟢 Free | Scroll storytelling (pin/scrub), timelines, SplitText, SVG morphs, non-React pages | Industry standard, now fully free incl. plugins; proprietary Webflow license. Pairs with `motion` | `animation` `scroll` `scrolltrigger` `splittext` `svg` |
| [`spline`](plugins/web-design/skills/spline/SKILL.md) | web-design | 🟡 Freemium | Interactive 3D heroes and product showcases embedded in Next.js | Fastest real 3D for sites; free plan has a watermark (Hobby ~$12/mo removes it); needs mobile fallback | `3d` `webgl` `hero` `interactive` |
| [`bklit-charts`](plugins/web-design/skills/bklit-charts/SKILL.md) | web-design | 🟢 Free | Charts and dashboards (shadcn registry): bar, area, line, pie, ring, radar, sankey, sparklines | Polished, free, MIT; links Bklit's official agent skills | `charts` `dashboards` `shadcn` `data-viz` |
| [`scroll-world`](plugins/web-design/skills/scroll-world/SKILL.md) | web-design | 🟠 Pay-per-use | Cinematic scroll-scrubbed "fly through the world" landing pages from AI-generated scenes and seamless camera clips | Impressive and well built; costs ~$11–30 per chain (mobile ~2x), approved up front. MIT | `scroll` `landing-pages` `ai-video` `cinematic` |
| [`design-skill-packs`](plugins/web-design/skills/design-skill-packs/SKILL.md) | web-design | 🟢 Free | Considering taste-skill, Impeccable, Anthropic's Frontend Design, UI/UX Pro Max or design-motion-principles in a project | Your design skills win; one pack per project. taste-skill is the best for landing pages (art direction + browser checks, MIT); Impeccable's slop detector is the best audit add; Frontend Design mostly redundant | `design` `anti-slop` `motion` `audit` `plugins` |
| [`design-md`](plugins/web-design/skills/design-md/SKILL.md) | web-design | 🟢 Free | Giving every project a DESIGN.md (tokens + rules) so agents stay on-brand; Awesome DESIGN.md as reference | Adopt the habit; use the 84 brand analyses for structure and principles, never to clone a brand. MIT | `design-system` `design-tokens` `design-md` `consistency` |
| [`refero`](plugins/web-design/skills/refero/SKILL.md) | web-design | 🟡 Freemium | Researching real product screens/flows and site styles before designing | Worth Pro ($120/yr) if designing often; use for patterns, never to clone brands | `design-research` `ui-patterns` `references` `mcp` `design-tokens` |
| [`penpot`](plugins/web-design/skills/penpot/SKILL.md) | web-design | 🟢 Free | Free Figma alternative; Claude reads/edits designs via the official MCP | Real free Figma alternative with CSS-native layouts; stay in Figma for Figma clients. MPL-2.0 | `design-tool` `figma-alternative` `mcp` `design-tokens` `design-to-code` |
| [`img2threejs`](plugins/web-design/skills/img2threejs/SKILL.md) | web-design | 🟢 Free | Turning a product photo or sketch into editable procedural Three.js code for a 3D hero | Clever, niche; heavy usage, not photoreal. Pinned project clone (its npx installer is global and unpinned). Apache-2.0 | `3d` `threejs` `image-to-3d` `procedural` `webgl` |
| [`open-higgsfield`](plugins/media-generation/skills/open-higgsfield/SKILL.md) | media-generation | 🟠 Pay-per-use | Generating lifelike AI video or photos via the self-hosted Open Higgsfield studio | Same output as Higgsfield, pay-per-use; the official plan is likely cheaper for heavy use. Unlicensed, unofficial | `ai-video` `ai-image` `higgsfield` `kling` `seedance` |
| [`voicestudio`](plugins/media-generation/skills/voicestudio/SKILL.md) | media-generation | 🟢 Free | Voiceovers, narration, voice cloning/design, dubbing, transcripts and subtitles, run locally | Credible, free ElevenLabs replacement for most work; ElevenLabs still wins on top-tier voices. AGPL | `tts` `voice-cloning` `dubbing` `transcription` `local-ai` |
| [`remotion`](plugins/media-generation/skills/remotion/SKILL.md) | media-generation | 🟡 Freemium | Videos with code in React: demos, promos, templated clips | Points to Remotion's official skills (not vendored, no upstream license); check Remotion's company license | `video` `react` `programmatic-video` |
| [`yt-dlp`](plugins/media-generation/skills/yt-dlp/SKILL.md) | media-generation | 🟢 Free | Downloading own/licensed video or audio, clips, subtitles for transcripts | The standard tool; legal use only (own, licensed, CC). Not a YouTube Premium replacement | `video` `download` `audio` `subtitles` `cli` |
| [`fooocus`](plugins/media-generation/skills/fooocus/SKILL.md) | media-generation | 🟢 Free | Free offline Midjourney-style images on a 4GB+ GPU | Good and free, but frozen on SDXL (LTS); Forge/ComfyUI for newer models | `ai-image` `stable-diffusion` `sdxl` `local-ai` `midjourney-alternative` |
| [`openseo`](plugins/seo/skills/openseo/SKILL.md) | seo | 🟠 Pay-per-use | Keyword/competitor research, SEO audits, rank tracking via self-hosted OpenSEO + its MCP | Legit Semrush replacement at low volume; you still pay DataForSEO per request. MIT | `seo` `keywords` `backlinks` `rank-tracking` `mcp` |
| [`technical-seo`](plugins/seo/skills/technical-seo/SKILL.md) | seo | 🟢 Free | Implementing SEO in code: metadata, sitemaps, canonicals, JSON-LD, Web Vitals, internal links (Next.js specifics) | The fix-it half; pair with openseo for data (from ECC) | `seo` `nextjs` `structured-data` `web-vitals` |
| [`plausible`](plugins/seo/skills/plausible/SKILL.md) | seo | 🟢 Free (self-host) | Cookieless, GDPR-friendly analytics on your and client sites | Default analytics; cloud for funnels/ecommerce, CE free for own sites. AGPL | `analytics` `privacy` `gdpr` `self-hosted` `ga-alternative` |
| [`weknora`](plugins/knowledge/skills/weknora/SKILL.md) | knowledge | 🟢 Free (self-host) | Q&A over a document set, "ask our docs" chatbots on client sites, client/project docs in Claude Code via MCP | Mature, free, self-hosted (Tencent, MIT). Bring your own models; heavy stack. Replaces Notion AI's Q&A, not Notion | `rag` `knowledge-base` `chatbot` `mcp` `self-hosted` |
| [`context7`](plugins/knowledge/skills/context7/SKILL.md) | knowledge | 🟡 Freemium | Current, version-specific docs for fast-moving libraries (Next.js, Tailwind, Supabase, Motion) | Worth enabling for web work; free key enough. Pin it (the promo's `@latest` isn't). Queries go to Upstash. MIT client | `docs` `libraries` `mcp` `up-to-date` `nextjs` |
| [`openwhispr`](plugins/productivity/skills/openwhispr/SKILL.md) | productivity | 🟡 Freemium | Hotkey voice dictation (including prompts into Claude Code), meeting transcription, notes | Real free Wispr Flow replacement with local models; Pro ($80/yr) only for cloud and sync. MIT | `dictation` `speech-to-text` `meetings` `local-ai` |
| [`openproject`](plugins/productivity/skills/openproject/SKILL.md) | productivity | 🟢 Free (self-host) | Self-hosted project management (Gantt, boards, time tracking) for team or client projects; Claude creates and updates tasks via REST API | Mature and free (GPL), but heavy and Jira-like; overkill solo, so use GitHub Projects then. MCP is Enterprise-only | `project-management` `gantt` `time-tracking` `self-hosted` |
| [`cal-com`](plugins/productivity/skills/cal-com/SKILL.md) | productivity | 🟡 Freemium | Booking pages, "book a call" on your or client sites (React embed), Calendly replacement | Excellent. Cloud free plan covers a solo user; self-hosted cal.diy is a stripped, non-production fork | `scheduling` `booking` `embeds` `calendly-alternative` |
| [`cap`](plugins/productivity/skills/cap/SKILL.md) | productivity | 🟡 Freemium | Screen recordings: instant share links, polished Studio demos, client walkthroughs | Great Loom replacement, but the free plan is personal-only; client work needs the $58 one-time license. AGPL | `screen-recording` `loom-alternative` `video` `async` |
| [`appflowy`](plugins/productivity/skills/appflowy/SKILL.md) | productivity | 🟡 Freemium | Private, local-first notes/docs/wiki workspace (Notion alternative) | Solid for own notes and wikis; tiny free cloud quota; Notion still wins on ecosystem. AGPL | `notes` `docs` `wiki` `notion-alternative` `local-first` |
| [`bitwarden`](plugins/productivity/skills/bitwarden/SKILL.md) | productivity | 🟡 Freemium | Passwords, client credential handover, keeping API keys out of .env and chat (Secrets Manager/CLI) | Best open-source password manager; free/Premium plenty. Dev win is secret injection | `passwords` `secrets` `security` `cli` `1password-alternative` |
| [`claude-peers`](plugins/productivity/skills/claude-peers/SKILL.md) | productivity | 🟢 Free | Separate Claude Code sessions messaging each other across projects | Clever but flagged: never with --dangerously-skip-permissions; native subagents and teams are safer. MIT | `multi-agent` `claude-code` `mcp` `coordination` `sessions` |
| [`google-workspace-cli`](plugins/productivity/skills/google-workspace-cli/SKILL.md) | productivity | 🟢 Free | Claude reading/triaging Gmail, checking Calendar, Drive files, Sheets and Docs from the terminal via `gws` | Best terminal route to Workspace; Google org but unofficial and pre-1.0. Narrow scopes, confirm before sending. Apache-2.0 | `google-workspace` `gmail` `calendar` `drive` `sheets` `cli` |
| [`obsidian`](plugins/productivity/skills/obsidian/SKILL.md) | productivity | 🟢 Free | Claude writing or organizing notes, Bases and canvases in an Obsidian vault | Points to kepano's official-adjacent skills (installed upstream). Only if you use Obsidian. MIT | `notes` `obsidian` `markdown` `pkm` |
| [`chatwoot`](plugins/customer-support/skills/chatwoot/SKILL.md) | customer-support | 🟢 Free (self-host) | Live chat on your or client sites, shared inbox (email, WhatsApp, social), help center | Mature free self-hosted Intercom replacement; AI and branding are paid. MIT core, commercial `enterprise/` | `live-chat` `helpdesk` `support-inbox` `widget` `self-hosted` |
| [`ollama`](plugins/local-ai/skills/ollama/SKILL.md) | local-ai | 🟢 Free | Local/offline AI: models for WeKnora/AppFlowy/n8n, local APIs, Claude Code on local models | Easiest local LLM runtime; free and private, but far weaker than Claude for agentic coding. MIT | `local-ai` `llm` `embeddings` `privacy` `ollama` |
| [`autoresearch`](plugins/local-ai/skills/autoresearch/SKILL.md) | local-ai | 🟠 Pay-per-use | Overnight autonomous LLM-training experiments on a rented GPU | Karpathy research toy; needs an H100-class GPU; isolate it (runs with permissions off). MIT | `ml-research` `llm-training` `autonomous-agents` `gpu` `experiments` |
| [`n8n`](plugins/automation/skills/n8n/SKILL.md) | automation | 🟢 Free (self-host) | Automating processes: forms to CRM, notifications, AI pipelines, webhooks, Zapier replacement | Best self-hostable Zapier alternative; fair-code: free for own/clients' internal use, not to resell. Includes n8n-MCP: dev instance only, telemetry off (it uploads sanitized workflows by default) | `automation` `workflows` `integrations` `webhooks` `self-hosted` `mcp` |
| [`cli-anything`](plugins/automation/skills/cli-anything/SKILL.md) | automation | 🟢 Free | Letting Claude drive desktop apps (Blender, GIMP, Inkscape, LibreOffice, Obsidian…) via agent CLIs | Useful; community CLIs are third-party code, so install one at a time, reviewed and pinned. Apache-2.0 | `automation` `cli` `desktop-apps` `agent-tools` `blender` |
| [`workflow-frameworks`](plugins/agent-workflows/skills/workflow-frameworks/SKILL.md) | agent-workflows | 🟢 Free | Bigger builds with a brainstorm → spec → plan → execute → verify loop: Superpowers or GSD | Both good; one per project, project scope. Superpowers lighter (but an always-on override skill); GSD (moved to open-gsd/gsd-core) heavier with ~30 hooks. MIT | `workflows` `planning` `spec-driven` `tdd` `subagents` |
| [`claude-mem`](plugins/agent-workflows/skills/claude-mem/SKILL.md) | agent-workflows | 🟡 Freemium | Memory across many sessions in a long project | Useful, but install with `--provider claude` and telemetry off (hosted and PostHog by default). Try CLAUDE.md + notes first. Apache-2.0 | `memory` `context` `sessions` `mcp` `claude-code` |

```
Skills/
├── .claude-plugin/marketplace.json     # marketplace "dean-skills"
├── inbox/                              # drop raw skills here, then "sort the inbox"
├── plugins/
│   ├── token-efficiency/
│   ├── code-audit/
│   ├── web-design/
│   ├── media-generation/
│   ├── seo/
│   ├── knowledge/
│   ├── productivity/
│   ├── customer-support/
│   ├── local-ai/
│   ├── automation/
│   └── agent-workflows/
│       ├── .claude-plugin/plugin.json
│       └── skills/<skill-name>/SKILL.md (+ SOURCE.md, scripts, references)
├── .claude/skills/add-skill/           # the /add-skill flow: review, categorize, place
├── templates/project-settings.json     # drop-in for a project's .claude/settings.json
└── CLAUDE.md                           # points Claude at the add-skill flow
```

## Install (terminal, Desktop app, IDE)

Inside a Claude Code session:

```
/plugin marketplace add DeanMcCoppin/Skills
/plugin install web-design@dean-skills
/plugin install code-audit@dean-skills
/plugin install token-efficiency@dean-skills
/plugin install media-generation@dean-skills
/plugin install seo@dean-skills
/plugin install knowledge@dean-skills
/plugin install productivity@dean-skills
/plugin install customer-support@dean-skills
/plugin install local-ai@dean-skills
/plugin install automation@dean-skills
/plugin install agent-workflows@dean-skills
```

Or from your shell:

```bash
claude plugin marketplace add DeanMcCoppin/Skills
claude plugin install web-design@dean-skills          # add --scope project to record it in the repo
```

Skills are namespaced by plugin, e.g. `/web-design:dean-design-taste`. Claude also picks them up automatically when a skill's description matches the task.

Update after pushing changes here: `claude plugin marketplace update dean-skills` (bump the plugin's `version` in `plugin.json`, or installed copies stay on the old version).

## Enable per project

Copy `templates/project-settings.json` into the project's `.claude/settings.json` (merge it if the file exists), and delete the plugins you don't want there:

```json
{
  "extraKnownMarketplaces": {
    "dean-skills": { "source": { "source": "github", "repo": "DeanMcCoppin/Skills" } }
  },
  "enabledPlugins": {
    "token-efficiency@dean-skills": true,
    "code-audit@dean-skills": true,
    "web-design@dean-skills": true,
    "media-generation@dean-skills": true,
    "seo@dean-skills": true,
    "knowledge@dean-skills": true,
    "productivity@dean-skills": true,
    "customer-support@dean-skills": true,
    "local-ai@dean-skills": true,
    "automation@dean-skills": true,
    "agent-workflows@dean-skills": true
  }
}
```

Because all plugins use relative paths inside this repo, once you trust the project folder Claude Code registers the marketplace and loads the enabled plugins. To switch one off just for yourself in a project, set it to `false` in `.claude/settings.local.json`.

### Cloud sessions (claude.ai/code) — read this

The current docs say cloud sessions **don't install plugins or marketplaces declared in a repo's `.claude/settings.json`** ([what carries over](https://code.claude.com/docs/en/cloud-environments#what-carries-over-from-your-setup)). The template above still does no harm there, but it won't load the skills. To get them in the cloud, either:

1. **Enable the skills on your claude.ai account** (skills settings on claude.ai, or **Customize** in the Desktop app; upload each skill folder). Cloud sessions, Cowork, and signed-in terminal sessions all load account skills. Frontmatter in this repo is kept to upload-safe keys for this reason.
2. **Commit the skills into the project** at `.claude/skills/<skill-name>/`. Cloud sessions load a repo's `.claude/skills/` (except in project threads). Example:
   ```bash
   cp -r ~/src/Skills/plugins/web-design/skills/* .claude/skills/
   ```

## Adding skills

Open this repo in Claude Code (terminal or cloud) and either:

- **Add one now**: "add this skill: <GitHub URL>", paste the skill text, or run `/add-skill <url or path>`.
- **Batch it**: drop folders, `SKILL.md` files, pasted text or a list of URLs into `inbox/`, then say **"sort the inbox"**.

Both run the same flow, defined in [`.claude/skills/add-skill/`](.claude/skills/add-skill/SKILL.md):

1. **Intake**: copies the skill into a quarantine folder outside the repo. Nothing from it is ever executed.
2. **Review**: Claude reads every file and reviews it against the [checklist](.claude/skills/add-skill/review-checklist.md): phoning home, `curl | sh`, rule overrides, credential access, hidden or encoded content. Flagged skills stop and wait for you.
3. **License**: skips anything that isn't permissively licensed.
4. **Filter**: picks a category by the skill's primary purpose ([categories.md](.claude/skills/add-skill/categories.md)). If it fits none, Claude asks and can create a new category plugin.
5. **Dedupe**: compares it with every existing skill and proposes one merged skill instead of two.
6. **Place**: kebab-case folder, clean frontmatter, a description that says *when* to trigger, supporting files alongside, and `SOURCE.md` with provenance (URL, author, license, changes) plus **notes**: verdict, strengths, weaknesses, alternatives.
7. **Finish**: adds a row to the [skills catalog](#skills-catalog), bumps the plugin version, runs `claude plugin validate`, and reports what was added, merged, rejected, and what needs your decision.

Then review it, and ask Claude to commit and push.

## Where to find more

- [Awesome Claude Code](https://github.com/hesreallyhim/awesome-claude-code): a curated directory of skills, plugins, hooks and workflows. It's CC BY-NC-ND, so it's linked, not copied: browse it, then add individual items here with the add-skill flow (each item's own license applies).
- Anthropic's official marketplace (`claude-plugins-official`, built into Claude Code): `/plugin` to browse.
- Not imported whole: Everything Claude Code (ECC, affaan-m/everything-claude-code). Its best skills were cherry-picked into this repo; installing it whole adds global hooks.

## Validate

```bash
claude plugin validate .
claude plugin validate ./plugins/web-design
```
