---
name: strategic-compact
description: Decide when to /compact a Claude Code session - at logical task boundaries (after research, after planning, after debugging, before switching tasks) instead of mid-task auto-compaction - and what to save to files first. Use in long sessions approaching context limits, when switching to unrelated work, after a milestone, or when answers start losing track of earlier details.
---

# Strategic compaction

Compact on purpose at task boundaries, instead of letting auto-compaction fire mid-task. Claude should **suggest** `/compact` (with a focus message) at these points; Dean decides.

## When to Activate

- Running long sessions that approach context limits (200K+ tokens)
- Working on multi-phase tasks (research → plan → implement → test)
- Switching between unrelated tasks within the same session
- After completing a major milestone and starting new work
- When responses slow down or become less coherent (context pressure)

## Why Strategic Compaction?

Auto-compaction triggers at arbitrary points:
- Often mid-task, losing important context
- No awareness of logical task boundaries
- Can interrupt complex multi-step operations

Strategic compaction at logical boundaries:
- **After exploration, before execution** — Compact research context, keep implementation plan
- **After completing a milestone** — Fresh start for next phase
- **Before major context shifts** — Clear exploration context before different task

## Compaction Decision Guide

Use this table to decide when to compact:

| Phase Transition | Compact? | Why |
|-----------------|----------|-----|
| Research → Planning | Yes | Research context is bulky; plan is the distilled output |
| Planning → Implementation | Yes | Plan is written down (a file, or the task list if you have one); free up context for code |
| Implementation → Testing | Maybe | Keep if tests reference recent code; compact if switching focus |
| Debugging → Next feature | Yes | Debug traces pollute context for unrelated work |
| Mid-implementation | No | Losing variable names, file paths, and partial state is costly |
| After a failed approach | Yes | Clear the dead-end reasoning before trying a new approach |

## What Survives Compaction

Understanding what persists helps you compact with confidence:

| Persists | Lost |
|----------|------|
| CLAUDE.md instructions | Intermediate reasoning and analysis |
| Files on disk | File contents you previously read |
| Memory files and auto-memory | Multi-step conversation context |
| Git state (commits, branches) | Tool call history and counts |
| The task list — **only if you have the todo tools** (see below) | Nuanced user preferences stated verbally |

> ### Don't rely on the task list surviving — it may not exist
>
> Claude Code **2.1.233 removed the todo/task tools by default** on Opus 4.8, Sonnet 5,
> Fable 5, Mythos 5 and newer models (`TodoWrite`, `TaskCreate/Get/Update/List`).
> `CLAUDE_CODE_ENABLE_TODO_TOOLS=1` brings them back, but that is a per-machine
> environment setting — **it does not travel with this skill**, so you cannot assume the
> reader has it.
>
> This matters because "my todo list survives compaction" is a reason people compact
> *instead of* writing state down. If the tools are absent there is no list to survive,
> and the plan is simply gone. **Write the plan to a file before compacting** — a file
> persists on every version and every model. Treat the task list as a convenience that
> may be missing, never as your durable record.

## Best Practices

1. **Compact after planning** — Once the plan is finalized **and written to a file**, compact to start fresh
2. **Compact after debugging** — Clear error-resolution context before continuing
3. **Don't compact mid-implementation** — Preserve context for related changes
4. **Write before compacting** — Save important context to files or memory before compacting
5. **Use `/compact` with a summary** — Add a custom message: `/compact Focus on implementing auth middleware next`

## Keeping baseline context small

- **CLAUDE.md is always loaded.** Keep it lean; move detail into skills, which load only when triggered.
- **Skills add context when loaded.** Avoid several skills that cover the same job (this repo's dedupe rule).
- **Tool results are the biggest consumers:** large file reads, broad searches and MCP responses. Read the ranges you need, and delegate wide searches to a subagent so only its conclusion comes back.
- **Duplicate instructions:** the same rules in user and project CLAUDE.md, or skills repeating CLAUDE.md. Remove the repeats.
- Use `/context` to see what's filling the window before deciding to compact.
