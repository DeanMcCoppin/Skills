# Source

- This skill: Dean (original), written with Claude on 2026-10-27. License: TODO (this repo has no LICENSE file yet).
- Purpose: Dean doesn't want to remember or call skills by name; this is the router Claude reads to pick skills itself. A project's `CLAUDE.md` (from `templates/CLAUDE.md`) tells Claude to load it.
- Maintenance: whenever a skill is added, merged, renamed or removed in this repo, update the routing here in the same change (the add-skill flow's finish step says so).

## Notes

- Why a router as well as good descriptions: descriptions make single skills trigger, but they don't give an order (brief → design → build → check → ship) or say which skill wins when several match. The playbook does both, and holds the "ask Dean first" rules in one place.
- Cost: ~1,500 tokens when loaded; only loaded on substantial tasks.
