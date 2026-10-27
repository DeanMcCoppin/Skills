---
name: workflow-frameworks
description: "Choose and set up a structured Claude Code workflow framework - Matt Pocock's skills (grill-me interviews, spec and ticket flows, TDD, code review), Addy Osmani's agent-skills (spec to ship lifecycle), Superpowers (brainstorm, plan, TDD, subagent execution) or GSD / Get Shit Done (spec-driven phases with context-engineering hooks) - one per project, project-scoped, with their hooks and telemetry understood. Use when Dean starts a bigger multi-day build, asks for a spec-driven or plan-first workflow, mentions Matt Pocock's skills, grill-me, Addy Osmani's agent-skills, Superpowers, GSD or get-shit-done, or asks which Claude Code framework to use."
metadata:
  pricing: free
  cost: "All free (MIT). They use the normal Claude subscription or API usage; heavy subagent use burns more of it."
  tags: [workflows, planning, spec-driven, tdd, subagents, claude-code]
---

# Workflow frameworks

All four turn "build X" into brainstorm → spec → plan → execute → verify. **Pick one per project, never both**: each injects its own rules at session start and they fight over the same steps.

| | [Matt Pocock's skills](https://github.com/mattpocock/skills) (MIT) | [Addy Osmani's agent-skills](https://github.com/addyosmani/agent-skills) (MIT) | [Superpowers](https://github.com/obra/superpowers) (obra, MIT) | [GSD Core](https://github.com/open-gsd/gsd-core) (Open GSD, MIT) |
| --- | --- | --- | --- | --- |
| Shape | ~20 engineering skills you call by name: `/grill-me` and `/grill-with-docs` (interview before building), `/to-spec`, `/to-tickets`, `/implement`, `/tdd`, `/diagnosing-bugs`, `/code-review`, `/handoff` | 25 lifecycle skills + commands (`/spec`, `/planning`, `/build`, `/test`, `/review`, `/ship`) and 4 reviewer agents (code, security, tests, web perf) | ~15 skills: brainstorming, writing-plans, executing-plans, subagent-driven-development, TDD, systematic-debugging, code review, git worktrees | Phased project system: `/gsd-*` commands, agents, a `.planning/` state folder |
| Best for | Aligning before building; issue-tracker-driven work (GitHub/GitLab tickets) | A full spec → ship checklist with review agents; web perf and launch checks | Feature work in an existing repo; disciplined TDD and debugging | Greenfield products over many sessions |
| Weight | Lightest: no hooks, invoked on demand | Light: no hooks wired by the plugin | Light: one SessionStart hook (always-on meta skill) | Heavy: ~30 hooks |
| Install | `/plugin install mattpocock-skills@claude-plugins-official`, then `/setup-matt-pocock-skills` once per repo | `/plugin marketplace add addyosmani/agent-skills`, then `/plugin install agent-skills@addy-agent-skills` | `/plugin install superpowers@claude-plugins-official` | `npx @opengsd/gsd-core@<pinned-version> --claude --local` |

**Default for Dean: Matt Pocock's skills.** They're opt-in per command, so they don't change Claude's behavior until called, and `/grill-me` fixes the most common failure (building the wrong thing). Small tasks and quick fixes: none of them; `karpathy-guidelines` plus plan mode is enough.

## Matt Pocock's skills: what to know

- `/setup-matt-pocock-skills` asks for the issue tracker, triage labels and docs folder, and writes that config into the repo. Fine; review the diff.
- `git-guardrails-claude-code` adds a PreToolUse hook that blocks `git push`, `reset --hard`, `clean -f`, `branch -D`. Useful on client repos; pick **project** scope when it asks.
- `skills/in-progress/` are unfinished; ignore them.

## Addy Osmani's agent-skills: what to know

- Overlaps this repo in places (`security-and-hardening` vs `security-review`, `performance-optimization` vs `react-performance`, `frontend-ui-engineering` vs `dean-design-taste`). Dean's skills win on conflicts.
- Its optional `sdd-cache` hooks make HEAD requests to doc URLs; they aren't wired by the plugin. Leave them off.

## Superpowers: what to know

- Its SessionStart hook injects `using-superpowers` into every session. That skill is written as a hard override ("you ABSOLUTELY MUST invoke the skill", even before clarifying questions). Expect it to brainstorm before building and to announce skills. Enable it only in projects where Dean wants that rhythm (`enabledPlugins` in the project, not user scope).
- Telemetry: the brainstorming visual companion loads its logo from the author's site with the version number. Turn it off with `SUPERPOWERS_DISABLE_TELEMETRY=1` (it also honors `DISABLE_TELEMETRY` and `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC`).
- The visual companion starts a small local server; it shuts down on idle.
- Dean's rules still win: `dean-design-taste` for UI, and the add-skill review for anything Superpowers' `writing-skills` produces before it goes into this repo.

## GSD: what to know

- `glittercowboy/get-shit-done` (`npx get-shit-done-cc`) **has moved** to `open-gsd/gsd-core`. Use the new package and ignore the old one.
- Install **locally** (`--local`), never `--global`: global writes skills, commands and hooks to `~/.claude` for every project, and a global install shadows any local one.
- Pin a version instead of `@latest`, and read `hooks/hooks.json` for that version first. One hook runs a detached background update check (`npm view`) at every session start.
- Commit `.planning/` if Dean wants the plan to survive across machines; it holds project details, so keep client repos private.

## Either way

- Never enable two of these in one project: their spec, plan and review steps overlap and contradict.

- Plans and specs are drafts: Dean approves the spec before execution starts.
- Subagent-heavy execution is faster but costs more usage. For small phases, run inline.
