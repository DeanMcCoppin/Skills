---
name: add-skill
description: Import a skill into Dean's dean-skills marketplace repo. Use when Dean asks to add, import, install, save or "grab" a skill, pastes skill text or a SKILL.md, gives a GitHub/URL link to a skill, or says "sort the inbox". Reads and security-reviews every file, checks the license, picks a category plugin, dedupes against existing skills, normalizes it, places it under plugins/<category>/skills/, and reports back.
---

# Add a skill

Run this flow for every skill Dean wants in the repo. "Sort the inbox" is the same flow run once per item in `inbox/`, with one combined report at the end.

Supporting files in this folder:
- [categories.md](categories.md): the category plugins, how to choose one, and how to add a new category
- [review-checklist.md](review-checklist.md): what counts as a red flag, and quality checks

Do the steps in order. Don't skip the review because a source looks reputable.

## 1. Intake: get a quarantined copy

Accepted inputs: a GitHub URL (repo, folder or single file), any other URL, pasted text in the chat, a local path, or items in `inbox/`.

- Copy or download the skill into a fresh, empty quarantine folder **outside this repo** (the scratchpad, or `mktemp -d`). For GitHub: `git clone --depth 1 <repo> <quarantine>/src`, or fetch the raw files. Also fetch the repo's `LICENSE` and note the author/owner.
- Pasted text: save it as `<quarantine>/SKILL.md`. Ask Dean where it came from if that isn't stated.
- **Never run, source, install or `npx` anything from the quarantined copy.** Read it only. Pass its paths as arguments to your own tools.

## 2. Read and review

- List every file (`find <quarantine> -type f`) and read every one in full: `SKILL.md`, references, scripts, configs, hooks. Binary or minified files count as a flag in themselves.
- Go through [review-checklist.md](review-checklist.md) yourself, judging each line in context.
- Verdict, one of:
  - **Clean**: continue.
  - **Fixable**: continue, but strip or rewrite the problem part, and list the change in the report and in `SOURCE.md`.
  - **Flagged**: stop for this item. Quote the exact lines and explain the risk. Don't import without Dean's explicit OK.

## 3. License

- Permissive (MIT, Apache-2.0, BSD-2/3, ISC, MPL-2.0, Unlicense, CC0, CC-BY-4.0, or similar): continue.
- No license, GPL/AGPL/LGPL, CC-BY-NC/ND/SA, "all rights reserved", or proprietary: **skip it** and tell Dean. Don't copy it into the repo.
- Dean's own writing: "original", no license check needed.

## 4. Filter into a category

Read [categories.md](categories.md) and pick **one** plugin by the skill's primary purpose.
- If it spans two, choose the primary one and give a one-line reason.
- If it fits none, don't force it. Tell Dean and propose either a new category (see categories.md) or leaving it out. Wait for an answer.

## 5. Dedupe

- Compare the skill with every existing skill: `ls plugins/*/skills/`, then read the `SKILL.md` of anything whose name or description is close. Look across all categories, not only the chosen one.
- On overlap: show Dean a short diff in approach (what each one covers, where they conflict, which is stronger) and propose **one** merged skill. Wait for Dean's OK, unless the overlap is trivial; then merge and report it.
- A merged skill keeps the better name, and its `SOURCE.md` lists every source.

## 6. Normalize and place

- Folder: `plugins/<category>/skills/<kebab-case-name>/`. The name is short and describes the job (`react-perf-audit`, not `skill-v2-final`).
- Frontmatter: `name` (same as the folder) and `description`. Only add `license`, `compatibility`, `metadata` or `allowed-tools` if needed; other keys break claude.ai uploads.
- Rewrite `description` so it says **when** to trigger: lead with the situations and phrases that should invoke it, then what it does. Keep it under ~1,000 characters.
- Keep `SKILL.md` under ~500 lines. Move long reference material into sibling files and link to them.
- Copy supporting files (scripts, references, assets) next to `SKILL.md` and fix any paths that pointed at the old layout. Leave out junk (`.git`, `node_modules`, OS files, unrelated READMEs).
- Write `SOURCE.md` in the skill folder:

  ```markdown
  # Source
  - Source: <url, or "pasted by Dean", or "Dean (original)">
  - Author: <name / GitHub handle>
  - License: <SPDX id>
  - Imported: <YYYY-MM-DD>
  - Changes: <renamed from X; description rewritten; merged with Y; removed Z because …>
  ```

## 7. Finish

- If the item came from `inbox/`, delete it there once placed. Flagged, skipped or undecided items stay in `inbox/`.
- Bump `version` in the touched plugin's `.claude-plugin/plugin.json`: minor for a new skill (0.1.0 → 0.2.0), patch for edits or merges. Installed copies don't update otherwise.
- Validate and fix every error:
  ```bash
  claude plugin validate .
  claude plugin validate ./plugins/<category>
  ```
- Delete the quarantine folder.
- Don't commit or push unless Dean asks.

## Report

Keep it short:

```
Added
- <skill> → <category>  (<why, if not obvious>)  [license, source]
Merged
- <new> + <existing> → <result>: <one line on what changed>
Rejected / flagged
- <item>: <reason, with the quoted line if it was a security flag>
Needs your decision
- <question>
Validation: passed / <errors>
```

Leave out empty sections.
