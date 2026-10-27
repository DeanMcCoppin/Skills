---
name: workflow-frameworks
description: "Choose and set up a structured Claude Code workflow framework - Superpowers (brainstorm, plan, TDD, subagent execution, review) or GSD / Get Shit Done (spec-driven phases with context-engineering hooks) - one per project, project-scoped, with their hooks and telemetry understood. Use when Dean starts a bigger multi-day build, asks for a spec-driven or plan-first workflow, mentions Superpowers, GSD or get-shit-done, or asks which Claude Code framework to use."
metadata:
  pricing: free
  cost: "Both free (MIT). They use the normal Claude subscription or API usage; heavy subagent use burns more of it."
  tags: [workflows, planning, spec-driven, tdd, subagents, claude-code]
---

# Workflow frameworks: Superpowers vs GSD

Both turn "build X" into brainstorm → spec → plan → execute → verify. **Pick one per project, never both**: each injects its own rules at session start and they fight over the same steps.

| | [Superpowers](https://github.com/obra/superpowers) (obra, MIT) | [GSD Core](https://github.com/open-gsd/gsd-core) (Open GSD, MIT) |
| --- | --- | --- |
| Shape | ~15 skills: brainstorming, writing-plans, executing-plans, subagent-driven-development, TDD, systematic-debugging, code review, git worktrees, verification | Phased project system: `/gsd-*` commands, agents, a `.planning/` state folder (PROJECT, ROADMAP, phases) |
| Best for | Feature work in an existing repo; disciplined TDD and debugging | Greenfield products over many sessions; keeping state when context resets |
| Weight | Light: one SessionStart hook | Heavy: ~30 hooks (statusline, read/write/prompt guards, context monitor, update check, commit validation) |
| Install | `/plugin install superpowers@claude-plugins-official` | `npx @opengsd/gsd-core@<pinned-version> --claude --local` |

Small tasks and quick fixes: use neither. `karpathy-guidelines` plus plan mode is enough.

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

- Plans and specs are drafts: Dean approves the spec before execution starts.
- Subagent-heavy execution is faster but costs more usage. For small phases, run inline.
