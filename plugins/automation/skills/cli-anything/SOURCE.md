# Source

- Tool: https://github.com/HKUDS/CLI-Anything
- Author: HKUDS (Data Intelligence Lab, University of Hong Kong) and community contributors
- License: Apache-2.0
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at 34f5195 (LICENSE, README quick start, Claude Code section, news).
- Promo note: "same authors" as OpenSpace (HKUDS).

## Notes

- Verdict: useful for making desktop apps scriptable by Claude (images, 3D, documents). The hub's community CLIs are third-party code, so install them one at a time and review them.
- Good at:
  - many app harnesses with tests
  - a SKILL.md per CLI
  - --json output
  - a generator for new CLIs
  - active security fixes (path traversal, injection)
- Weak at / risks:
  - community supply chain: each CLI is someone's code running locally
  - the meta-skill can auto-install CLIs (avoid)
  - wrapped apps must be installed separately
  - quality varies per harness
- Alternatives: the app's own API or MCP (n8n, Penpot, Obsidian REST); plain scripts with the app's CLI (Blender `-b`, LibreOffice `--headless`); `rea-reverse-engineering` to inspect a harness
