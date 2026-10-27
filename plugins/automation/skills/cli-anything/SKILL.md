---
name: cli-anything
description: "Let Claude Code drive desktop and backend software through agent-native CLIs from CLI-Anything (HKUDS) - ready-made harnesses for Blender, GIMP, Inkscape, LibreOffice, Krita, Obsidian, Zotero, n8n, Zoom, FreeCAD, Godot and more via the CLI-Hub, or generate a new CLI for any app or codebase. Use when Dean wants Claude to operate a desktop app (batch-edit images, render a Blender scene, convert documents, script Obsidian), automate software that has no API, or mentions CLI-Anything or CLI-Hub."
metadata:
  pricing: free
  cost: "Free (Apache-2.0). Wrapped apps keep their own licenses and costs."
  tags: [automation, cli, desktop-apps, agent-tools, blender]
---

# CLI-Anything

[HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything) (Apache-2.0) wraps real software in command-line "harnesses" with a SKILL.md each, so an agent can run them like any CLI. The **CLI-Hub** is a registry of community-built ones.

## Rules: community code runs on Dean's machine

- **Never install the whole hub, and never use `-g -y` installs of the meta-skill** that let an agent pick and install CLIs on its own. Install one CLI at a time, chosen by Dean.
- Before installing a CLI, run `cli-hub info <name>` and read its source (repo, package, install command) and its SKILL.md. Check that it only talks to the local app or the services it claims, and that write or destructive commands are clearly marked.
- Pin versions (`pip install cli-anything-<name>==<version>` or the hub's equivalent) and update deliberately.
- Work on copies of files: render or export into a new folder, and keep originals untouched. Many harnesses can overwrite projects or libraries.
- Credentials (Zoom, cloud tools) go into the CLI's own config by Dean, never into chat.

## Use an existing CLI

```bash
pip install cli-anything-hub          # the hub client
cli-hub search image                  # find one
cli-hub info gimp                     # inspect: source, commands, requirements
cli-hub install gimp                  # install the chosen one (the upstream app must be installed too)
```

Then ask Claude to use it ("resize and watermark every image in ./shoot with the GIMP CLI, output to ./web"). Most harnesses offer `--json` output, previews and a REPL.

## Build a new CLI

For an app or internal tool with no harness yet, install CLI-Anything's own Claude Code plugin from its marketplace (see the repo's "Claude Code" section). Then run its generator, which works through 7 phases: analyze, design commands, implement, test, write SKILL.md, publish. Review the generated code like any PR, and keep it local unless Dean wants to contribute it.

## Good fits for Dean

- Image batches for sites (GIMP, Krita, Inkscape for SVG cleanup), Blender product renders, LibreOffice document conversion (proposals to PDF), Obsidian or Zotero notes, n8n workflow management, subtitle and video tools.
- If the app has a good API or MCP server already (n8n, Penpot), prefer that over a wrapper.
