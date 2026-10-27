# Bootstrap: set up a project with Dean's skills

**For Claude**, working in a new or existing project (not this repo). Dean will say something like "set up this project with my skills: https://github.com/DeanMcCoppin/Skills". Do the following, then start the work with the `playbook` skill.

## 1. Settings

Create or merge `.claude/settings.json` in the project:

```json
{
  "extraKnownMarketplaces": {
    "dean-skills": { "source": { "source": "github", "repo": "DeanMcCoppin/Skills" } }
  },
  "enabledPlugins": {
    "agent-workflows@dean-skills": true,
    "token-efficiency@dean-skills": true,
    "code-audit@dean-skills": true,
    "web-design@dean-skills": true,
    "seo@dean-skills": true,
    "knowledge@dean-skills": true,
    "productivity@dean-skills": true,
    "customer-support@dean-skills": true,
    "automation@dean-skills": true,
    "media-generation@dean-skills": true,
    "local-ai@dean-skills": true
  }
}
```

Enable **all** plugins by default: the playbook decides what to use, and every skill's description together costs only about 7k tokens. Merge with existing settings; never remove what's there.

## 2. CLAUDE.md

Add the contents of [`templates/CLAUDE.md`](templates/CLAUDE.md) to the project's `CLAUDE.md` (create it, or append under its own heading). Fill in "This project" after the brief.

## 3. Load the skills

- **Terminal, Desktop app, IDE**: tell Dean to restart Claude Code in the project (or run `/plugin marketplace add DeanMcCoppin/Skills` once if it was never added) and trust the folder. The plugins then load. Check with `/plugin`.
- **Cloud session (claude.ai/code)**: plugins from settings don't load there. Copy the skills into the project instead, after Dean says yes (it adds files to the repo):
  ```bash
  git clone --depth 1 https://github.com/DeanMcCoppin/Skills /tmp/dean-skills
  mkdir -p .claude/skills && cp -r /tmp/dean-skills/plugins/*/skills/* .claude/skills/
  ```
  Then the `playbook` skill is at `.claude/skills/playbook`.

## 4. Start

Load `playbook`, ask Dean the start-of-project questions in one batch (with recommended defaults), then work through it.
