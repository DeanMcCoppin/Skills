---
name: skill-discovery
description: "Find skills, plugins, hooks and MCP servers for a task or project - Anthropic's claude-code-setup recommender (read-only scan of a codebase that suggests the top automations), Vercel's skills CLI (npx skills find / skills.sh leaderboard), the official plugin marketplace and Awesome Claude Code - and route every find through Dean's add-skill review instead of installing it straight away. Use when Dean asks 'is there a skill for X', 'find a skill', 'what should I set up for this project', 'recommend automations/hooks/MCP servers', or mentions skills.sh, npx skills or claude-code-setup."
metadata:
  pricing: free
  cost: "Free. claude-code-setup Apache-2.0 (Anthropic); skills CLI MIT (Vercel), anonymous telemetry unless disabled."
  tags: [skills, discovery, plugins, mcp, hooks, setup]
---

# Skill discovery

**Check Dean's own marketplace first** (`dean-skills` catalog in its README). Then look outside. Anything found outside is a *candidate*: it gets imported through the `add-skill` flow in Dean's Skills repo (review, license, dedupe), not installed on the spot.

## "What should this project have?" → claude-code-setup

```
/plugin install claude-code-setup@claude-plugins-official
```
Then: "recommend automations for this project". Its `claude-automation-recommender` skill scans the repo (package files, frameworks, tests) and proposes the top 1–2 hooks, subagents, skills, plugins and MCP servers. It's **read-only** (it changes nothing). Map each suggestion to an existing Dean skill when one covers it (for example `context7`, `playwright-cli`, `security-review`); only the gaps become add-skill candidates.

## "Is there a skill for X?" → skills CLI (search only)

```bash
DISABLE_TELEMETRY=1 npx skills@1.7.4 find "<query>"      # or browse https://skills.sh
DISABLE_TELEMETRY=1 npx skills@1.7.4 use <owner/repo>@<skill>   # print a skill's prompt to read it, no install
```

- Telemetry: the CLI sends anonymous usage data and security-audit requests unless `DISABLE_TELEMETRY=1` or `DO_NOT_TRACK=1`.
- **Never `npx skills add … -g -y`.** Vercel's own `find-skills` skill tells agents to install globally and skip confirmation; that bypasses review and writes into every project. If Dean wants one in a project without importing it, `npx skills add <source> --skill <name> -a claude-code` (project scope, with prompts), after reading it.
- Install counts and stars are weak signals (several popular repos show inflated or inconsistent star counts). Read the files.

## Other places to look

- Anthropic's official marketplace: `/plugin` → browse `claude-plugins-official`; and `anthropic-skills` for anthropics/skills.
- [Awesome Claude Code](https://github.com/hesreallyhim/awesome-claude-code) (CC BY-NC-ND: link only, check each item's own license).
- [Awesome DESIGN.md](https://github.com/VoltAgent/awesome-design-md) for design systems (see `design-md`).

## Report back

For each candidate: what it does, source and license, one-line verdict, and whether a Dean skill already covers it. Then offer to import it with add-skill.
