# Skills

My personal Claude Code skills, packaged as a plugin marketplace called **`dean-skills`**. Skills are grouped into plugins so each category can be turned on per project.

| Plugin | What's in it |
| --- | --- |
| `token-efficiency` | Context management, concise output, compaction, cheaper workflows |
| `code-audit` | Reviews, security, performance, accessibility, dead code, dependency checks |
| `web-design` | UI/UX, typography, layout, Tailwind, Framer Motion, maps, landing pages |
| `media-generation` | AI image, video and voice generation (Open Higgsfield, VoiceStudio, model choice, prompting) |
| `seo` | Keyword and competitor research, site audits, rank tracking, local SEO, AI visibility (OpenSEO) |

## Skills catalog

One line per skill. The full verdict (strengths, weaknesses, alternatives) is in each skill's `SOURCE.md`.

| Skill | Plugin | Use it when | Verdict |
| --- | --- | --- | --- |
| [`dean-design-taste`](plugins/web-design/skills/dean-design-taste/SKILL.md) | web-design | Any web UI work. Sets my default stack, look and motion rules | Baseline for every frontend; fonts and colors still TODO |
| [`editorial-themes`](plugins/web-design/skills/editorial-themes/SKILL.md) | web-design | Building a full premium "theme" site for a business (law, agency, architect, restaurant…) in a Lexington-like editorial style | Strong for marketing sites; overkill for app UIs |
| [`open-higgsfield`](plugins/media-generation/skills/open-higgsfield/SKILL.md) | media-generation | Generating lifelike AI video or photos via the self-hosted Open Higgsfield studio | Same output as Higgsfield, pay-per-use; the official plan is likely cheaper for heavy use. Unlicensed, unofficial |
| [`voicestudio`](plugins/media-generation/skills/voicestudio/SKILL.md) | media-generation | Voiceovers, narration, voice cloning/design, dubbing, transcripts and subtitles, run locally | Credible, free ElevenLabs replacement for most work; ElevenLabs still wins on top-tier voices. AGPL |
| [`openseo`](plugins/seo/skills/openseo/SKILL.md) | seo | Keyword/competitor research, SEO audits, rank tracking via self-hosted OpenSEO + its MCP | Legit Semrush replacement at low volume; you still pay DataForSEO per request. MIT |

```
Skills/
├── .claude-plugin/marketplace.json     # marketplace "dean-skills"
├── inbox/                              # drop raw skills here, then "sort the inbox"
├── plugins/
│   ├── token-efficiency/
│   ├── code-audit/
│   ├── web-design/
│   ├── media-generation/
│   └── seo/
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
    "seo@dean-skills": true
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

## Validate

```bash
claude plugin validate .
claude plugin validate ./plugins/web-design
```
