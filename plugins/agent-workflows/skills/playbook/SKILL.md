---
name: playbook
description: "Dean's master routing guide for the dean-skills marketplace: which skills and tools to use, in what order, for any project or task (new website or landing page, web app, redesign, audit, SEO, content, automation, media, client handover), what to set up per project, and what needs Dean's OK first. Use at the start of every new project or substantial task, whenever Dean describes a goal without naming skills, when unsure which skill applies, or when Dean says 'set up this project', 'use my skills' or 'do it the best way'."
metadata:
  pricing: free
  cost: "Free. Points to other skills; some of those cost money, and this guide says when to ask."
  tags: [routing, workflow, orchestration, project-setup, defaults]
---

# Playbook

Dean doesn't remember skill names, so **Claude picks the skills**. For every substantial task: find the task type below, load the skills it lists (in order), and say in one line which ones you're using. Small tasks (a typo, one quick fix) skip the ceremony; `karpathy-guidelines` still applies.

Skill names below are dean-skills skills unless marked *(external)*. If a listed skill isn't loaded, its plugin isn't enabled in this project: tell Dean which plugin to enable (`<plugin>@dean-skills` in `.claude/settings.json`) rather than working without it.

## Always on

- `karpathy-guidelines`: ask instead of assuming, minimum code, surgical diffs, verifiable goals.
- `dean-design-taste` for anything visual; Dean's skills override third-party packs.
- `strategic-compact` in long sessions.
- Security: `security-review` whenever auth, payments, uploads, secrets or API routes are touched.

## Ask Dean first (never assume)

- Anything that **costs money** (paid APIs, generations, plans, GPU rental): give the cost estimate first.
- Installing global tools, hooks or MCP servers, creating accounts, signing in anywhere, sending email or messages, publishing or deploying.
- Using a third-party design pack, workflow framework or memory tool in the project (one of each at most).
- Anything flagged in a skill's guardrails.

Ask in **one batch** at the start of a project, with a recommended default for each, so Dean answers once.

## New website or landing page

1. **Brief**: interview Dean briefly (goal, audience, pages, the one action, brand assets, budget). Use `/grill-me` *(external, Matt Pocock's skills, see `workflow-frameworks`)* if installed; otherwise ask the same questions in one batch.
2. **Set up the project**: Next.js + Tailwind + Framer Motion per `dean-design-taste`; `context7` for current docs; `playwright-cli` so you can see what you build. Offer both setups in the start-of-project question batch.
3. **Design direction**: `refero` (real references) → `design-md` (write the project's DESIGN.md) → for marketing sites with no brand yet, offer `design-skill-packs` → taste-skill. Premium business sites (law, agency, architect, restaurant): `editorial-themes`.
4. **Build**: components from `component-libraries` (and `bencho-blocks` for tactile moments), animation with `motion` (React) or `gsap` (scroll storytelling), 3D with `spline` or `img2threejs`, charts `bklit-charts`, cinematic scroll pages `scroll-world` (pay-per-use, ask). Booking: `cal-com`. Live chat: `chatwoot`. Forms → automations: `n8n`.
5. **Media**: images or video via `media-generation` skills (`open-higgsfield`, `fooocus`, `remotion`, `voicestudio`): ask before anything paid.
6. **Check while building**: `playwright-cli` screenshots at 390 / 768 / 1440 after each section; `interface-polish` pass; `design-system` AI-slop check.
7. **Before shipping**: `accessibility`, `react-performance`, `technical-seo`, `plausible` (analytics), `security-review` if there's any backend, then `production-audit` for the ship/block verdict.
8. **After deploy**: `browser-qa` on the live URL.

## Web app or dashboard

Same as above, plus: `workflow-frameworks` (spec → plan → build; default Matt Pocock's skills) for anything over a day's work; `security-review` from the start; `e2e-testing` for critical flows; `bklit-charts` for dashboards; `google-workspace-cli`, `n8n` for integrations; `bitwarden` for secrets.

## Redesign or "it looks generic"

`design-system` (audit and extract tokens) → `refero` → `design-md` → rebuild with step 4 above → `interface-polish` → `playwright-cli` before/after screenshots. Impeccable's detector (`design-skill-packs`) for a rules-based slop report.

## Existing or unfamiliar codebase

`graphify` (big repos) or plain search → `karpathy-guidelines` for changes → `rea-reverse-engineering` only to inspect what third-party code does, on Dean's own or authorized targets.

## Audit or "is it ready?"

`production-audit` (overall verdict) with `security-review`, `accessibility`, `react-performance`, `technical-seo`, `mcp-dependency-review` (if `.mcp.json` changed), `browser-qa` (live URL).

## SEO and growth

`technical-seo` (fix in code) + `openseo` (keyword and competitor data, pay-per-use, ask) + `plausible` (analytics). Research what people say: `agent-reach` (public channels only).

## Other jobs

| Dean wants… | Use |
| --- | --- |
| Documents (proposal, invoice, deck, PDF) | `anthropic-skills` → document skills |
| Automate a process, connect apps | `n8n` (+ n8n-MCP on a dev instance) |
| Email, calendar, Drive, Sheets | `google-workspace-cli` |
| Read a social post, video transcript | `agent-reach`, `yt-dlp` |
| Docs chatbot or knowledge base | `weknora`; current library docs: `context7` |
| Video, voice, images | `remotion`, `voicestudio`, `open-higgsfield`, `fooocus` |
| Local or private AI | `ollama` |
| Project management, booking, notes | `openproject`, `cal-com`, `obsidian` / `appflowy` |
| Screen recording, dictation | `cap`, `openwhispr` |
| Hand a repo to another chat model | `repomix` |
| Shorter answers | `caveman` or `token-budget-advisor`, only when Dean asks |
| Design in a tool, not code (Figma alternative) | `penpot` |
| Claude driving desktop apps (Blender, GIMP, LibreOffice…) | `cli-anything` |
| Remember decisions across many sessions | `CLAUDE.md` / notes first; `claude-mem` only if Dean wants it (ask) |
| Hitting context or usage limits on log/data-heavy work | `strategic-compact`, then `headroom` (ask; it proxies all traffic) |
| Several Claude sessions coordinating | subagents first; `claude-peers` only if Dean asks |
| Automatic skill retrieval and evolution | `openspace` (experimental, ask) |
| Overnight ML training experiments | `autoresearch` (rented GPU, ask) |
| A skill or tool that isn't here | `skill-discovery`, then import through the Skills repo's add-skill flow |

## Reporting

At the end of each phase, tell Dean in plain words: what was done, which skills were used, what's left, and anything that needs a decision. No skill jargon needed; Dean cares about the result.
