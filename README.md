# claude-skills

My personal Claude Code skills, packaged as a plugin marketplace called **`dean-skills`**. Skills are grouped into three plugins so each category can be turned on per project.

| Plugin | What's in it |
| --- | --- |
| `token-efficiency` | Context management, concise output, compaction, cheaper workflows |
| `code-audit` | Reviews, security, performance, accessibility, dead code, dependency checks |
| `web-design` | UI/UX, typography, layout, Tailwind, Framer Motion, maps, landing pages |

```
claude-skills/
├── .claude-plugin/marketplace.json     # marketplace "dean-skills"
├── inbox/                              # drop raw skills here, then "sort the inbox"
├── plugins/
│   ├── token-efficiency/
│   ├── code-audit/
│   └── web-design/
│       ├── .claude-plugin/plugin.json
│       └── skills/<skill-name>/SKILL.md (+ SOURCE.md, scripts, references)
├── templates/project-settings.json     # drop-in for a project's .claude/settings.json
└── CLAUDE.md                           # tells Claude how to sort the inbox
```

## Install (terminal, Desktop app, IDE)

Inside a Claude Code session:

```
/plugin marketplace add DeanMcCoppin/claude-skills
/plugin install web-design@dean-skills
/plugin install code-audit@dean-skills
/plugin install token-efficiency@dean-skills
```

Or from your shell:

```bash
claude plugin marketplace add DeanMcCoppin/claude-skills
claude plugin install web-design@dean-skills          # add --scope project to record it in the repo
```

Skills are namespaced by plugin, e.g. `/web-design:dean-design-taste`. Claude also picks them up automatically when a skill's description matches the task.

Update after pushing changes here: `claude plugin marketplace update dean-skills` (bump the plugin's `version` in `plugin.json`, or installed copies stay on the old version).

## Enable per project

Copy `templates/project-settings.json` into the project's `.claude/settings.json` (merge it if the file exists), and delete the plugins you don't want there:

```json
{
  "extraKnownMarketplaces": {
    "dean-skills": { "source": { "source": "github", "repo": "DeanMcCoppin/claude-skills" } }
  },
  "enabledPlugins": {
    "token-efficiency@dean-skills": true,
    "code-audit@dean-skills": true,
    "web-design@dean-skills": true
  }
}
```

Because all three plugins use relative paths inside this repo, once you trust the project folder Claude Code registers the marketplace and loads the enabled plugins. To switch one off just for yourself in a project, set it to `false` in `.claude/settings.local.json`.

### Cloud sessions (claude.ai/code) — read this

The current docs say cloud sessions **don't install plugins or marketplaces declared in a repo's `.claude/settings.json`** ([what carries over](https://code.claude.com/docs/en/cloud-environments#what-carries-over-from-your-setup)). The template above still does no harm there, but it won't load the skills. To get them in the cloud, either:

1. **Enable the skills on your claude.ai account** (skills settings on claude.ai, or **Customize** in the Desktop app; upload each skill folder). Cloud sessions, Cowork, and signed-in terminal sessions all load account skills. Frontmatter in this repo is kept to upload-safe keys for this reason.
2. **Commit the skills into the project** at `.claude/skills/<skill-name>/`. Cloud sessions load a repo's `.claude/skills/` (except in project threads). Example:
   ```bash
   cp -r ~/src/claude-skills/plugins/web-design/skills/* .claude/skills/
   ```

## Adding skills: the inbox workflow

1. Drop anything into `inbox/`: a skill folder, a lone `SKILL.md`, a `.md`/`.txt` of pasted text, or a file listing GitHub URLs (you can also paste URLs in the chat).
2. Open this repo in Claude Code and say **"sort the inbox"**.
3. Claude follows `CLAUDE.md`:
   - reads every item fully and flags anything sketchy (phoning home, `curl | sh`, "ignore other rules", credential handling)
   - files each skill under the right plugin, or tells you it fits none
   - spots duplicates and proposes merging them into one stronger skill
   - normalizes names and frontmatter, rewrites descriptions to say *when* to trigger
   - writes `SOURCE.md` (URL, author, license) and skips anything without a permissive license
   - empties the inbox, validates, and gives you a summary of what went where
4. Review, then commit and push.

## Validate

```bash
claude plugin validate .
claude plugin validate ./plugins/web-design
```
