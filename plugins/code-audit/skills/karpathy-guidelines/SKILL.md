---
name: karpathy-guidelines
description: "Behavioral rules that prevent the classic LLM coding mistakes (from Andrej Karpathy's observations): state assumptions and ask instead of guessing, write the minimum code that solves the problem (reuse, platform features and existing dependencies before new code), make surgical diffs that touch only what the request needs, and turn tasks into verifiable goals (tests first). Use when writing, editing, reviewing or refactoring code, especially in existing codebases, when a change is growing beyond the request, or when a task is ambiguous."
license: MIT
metadata:
  pricing: free
  cost: "Free: behavioral guidelines (MIT)."
  tags: [coding-practices, simplicity, diffs, testing, guidelines]
---

# Karpathy Guidelines

Behavioral guidelines to reduce common LLM coding mistakes, derived from [Andrej Karpathy's observations](https://x.com/karpathy/status/2015883857489522876) on LLM coding pitfalls.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment. Worked examples (what goes wrong and the fix) are in [references/examples.md](references/examples.md).

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Take the first option that fully works (from Ponytail):
1. Does it need to exist? Skip what nobody asked for, and name it in one line.
2. Already in this codebase (helper, component, pattern)? Use it the way the surrounding code does.
3. Standard library or platform feature (a native `<input type="date">` before a date-picker library)?
4. An installed dependency? Never add a dependency for a few lines.
5. Otherwise, the minimum code that works.

Be lazy about the solution, never about the change: finish every caller, test and fixture the change touches. Never cut validation at trust boundaries, error handling that prevents data loss, security, accessibility, or anything the user asked for. A shortcut with a known limit gets a comment: `shortcut: <the limit>, <when to upgrade>`.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** diffs have fewer unnecessary changes, there are fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

In this repo's terms: pair with `production-audit` and `security-review` for what to check, and with `interface-polish` when the change is UI (polish is in scope only when asked).
