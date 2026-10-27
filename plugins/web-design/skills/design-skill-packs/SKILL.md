---
name: design-skill-packs
description: "Decide whether to add a third-party design skill pack to a project - taste-skill (art direction from a researched library + real-browser inspector), Impeccable (design commands + deterministic anti-slop detector), Anthropic's Frontend Design plugin, UI/UX Pro Max (searchable styles/palettes/fonts database) or design-motion-principles (motion audits) - what each adds, how to install it project-scoped, and why Dean's own design skills override them. Use when Dean asks for an extra design skill or plugin, mentions taste-skill, Impeccable, frontend-design, UI/UX Pro Max or design-motion-principles, or wants an automated design or motion audit."
metadata:
  pricing: free
  cost: "All five free (Apache-2.0, MIT, or bundled with Claude Code). Impeccable's Chrome/VS Code extensions are free too."
  tags: [design, ui, anti-slop, motion, audit, plugins]
---

# Design skill packs

**Dean's skills come first.** `dean-design-taste` (house style), `editorial-themes`, `motion`, `interface-polish` and `design-system` already cover direction, motion and polish. A pack is only worth adding for what those don't do, and **one pack per project at most**: two packs give Claude conflicting aesthetics. When a pack disagrees with Dean's skills, Dean's skills win.

| Pack | What it adds beyond Dean's skills | Install (per project) |
| --- | --- | --- |
| [taste-skill](https://github.com/Leonxlnx/taste-skill) (MIT) | **Art direction**: a script deals 3 of 20 researched directions (type, palette, hero, sections from 247 award sites), a subject-inventory and "idea" step, open-collection photos with credits, and a Chrome **inspector** that screenshots at 1440/768/390 and fails slop patterns. Separate rules for app screens | `/plugin marketplace add Leonxlnx/taste-skill`, then `/plugin install taste-skill@taste-skill` |
| [Impeccable](https://github.com/pbakaus/impeccable) (Apache-2.0) | A **deterministic detector** (62 rules, no LLM) that flags AI-slop patterns in code or a live page, plus commands like `/impeccable polish`, `audit`, `critique` and a `PRODUCT.md` brief | `npx impeccable@<pinned> install --providers=claude --scope=project` |
| Frontend Design (Anthropic, ships with Claude Code's official marketplace) | A short "avoid generic AI look" prompt: bold direction, distinctive type, no default purple gradients | `/plugin install frontend-design@claude-plugins-official` |
| [UI/UX Pro Max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (MIT) | A **local searchable database** (Python): ~80 styles, ~190 palettes, ~70 font pairings, chart and stack guidelines | `/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill`, then `/plugin install ui-ux-pro-max@ui-ux-pro-max-skill` |
| [design-motion-principles](https://github.com/kylezantos/design-motion-principles) (MIT) | A **motion audit** with an HTML report, using Emil Kowalski / Jakub Krehel-style principles | `npx skills add kylezantos/design-motion-principles` into the project, or copy its `skills/` folder |

## Which one, when

- **A marketing page or landing page that must not look AI-made, with no brand yet**: taste-skill. It's the strongest pack for pages: it makes the agent pick a direction, build from the client's real details, and check the result in a browser. With an existing brand, use `--keep palette,type`.

- **Auditing an existing UI for "AI look"**: Impeccable's detector (`npx impeccable detect`, the CLI or the Chrome extension). It's the only one that checks with rules instead of opinions, and pairs with `design-system`'s AI-slop check.
- **Exploring options for a new brand** (palettes, font pairs, style names): UI/UX Pro Max as a lookup tool, then bring the choice into `dean-design-taste` tokens. Don't let its presets override a direction Dean already set.
- **Motion feels off**: run `motion` first; add design-motion-principles only for a formal audit report to share with a client.
- **Frontend Design**: mostly duplicated by `dean-design-taste`. Skip it in Dean's projects; it's fine in throwaway prototypes without Dean's plugins.

## Install notes

- taste-skill installs nothing and uses no API keys. It needs Node 22+ and a local Chrome/Edge/Chromium. Its working files go in `.taste-skill/` in the project (gitignore it), and it keeps a draw history in `~/.taste-skill/history.json`. `assets.mjs` downloads photos from open collections (Openverse, Wikimedia, the Met, Art Institute of Chicago, Internet Archive, NASA) only when run, and records credits: keep the credits on the page. Its rules clash with Dean's in places ("decide instead of asking" on vague briefs, no rules or shadows, no small labels). Dean's skills and Dean's explicit brief win; for client briefs, ask anyway when the brief is ambiguous. Don't use its `install.sh` (it symlinks into global `~/.claude/skills`).

- Impeccable's launcher **downloads its engine binary on first run** into `~/.impeccable/bin/`, and the installer can write global harness folders (`~/.claude`). Use `--scope=project` and pin the version.
- Impeccable also installs a **PostToolUse/Stop hook** that runs its detector after UI edits (default yes). Keep it if the detector is why you installed it, or pass `--no-hooks`.
- Impeccable **telemetry is on by default**: new designs call its roll API at impeccable.style (always) and record which option won (opt-out). Turn the recording off with `npx impeccable telemetry off`, `IMPECCABLE_NO_TELEMETRY=1`, or `"telemetry": false` in the project's `.impeccable/config.json`. No code or file names are sent, per its docs.
- UI/UX Pro Max's `uipro` CLI is a global npm install; prefer the plugin route. Its search scripts run locally (no network).
- Pin `npx` versions instead of `@latest`, and enable packs in the project's `.claude/settings.json`, not user scope.
