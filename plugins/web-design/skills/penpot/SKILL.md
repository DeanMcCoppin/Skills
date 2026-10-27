---
name: penpot
description: "Design in Penpot (free, open-source Figma alternative built on web standards: SVG, CSS, flex/grid layouts, design tokens, components) and connect it to Claude Code with Penpot's official MCP server for design-to-code, code-to-design and design edits. Use when Dean wants a free Figma alternative, to turn a Penpot design into code, to have Claude read or update a design file, or mentions Penpot."
metadata:
  pricing: free
  cost: "Free and open source (MPL-2.0); cloud free plan and self-hosting available, paid plans for larger teams (check penpot.app/pricing)."
  tags: [design-tool, figma-alternative, mcp, design-tokens, design-to-code]
---

# Penpot

[penpot/penpot](https://github.com/penpot/penpot) (MPL-2.0) is a browser-based design and prototyping tool. Layouts are real CSS flex/grid, and it has native design tokens, so designs map closely to code.

## Use it

- Use the **cloud** (design.penpot.app) to start, or self-host with Docker (official docs) for full data control.
- Import Figma files with the official importer, or export from Figma to `.fig` and import. Check fonts, components and auto-layout after importing.
- Set up **design tokens** (colors, type, spacing, radii) in Penpot to match the project's Tailwind/CSS variables (`dean-design-taste`), so design and code share one source of truth.

## Connect Claude Code (official MCP)

[penpot/penpot-mcp](https://github.com/penpot/penpot-mcp) (MPL-2.0) has two parts: an MCP server, and a Penpot **plugin** that connects to it over WebSocket.
1. Clone the repo, `npm install`, then `npm run bootstrap` (Node 22), which builds and starts the MCP server and the plugin server.
2. In Penpot, load the plugin from the local plugin server, open it on the design file, and connect.
3. Add the MCP server to Claude Code with the URL and port the repo README gives, per project, with a reviewed commit or tag pinned (see `mcp-dependency-review`).

Then Claude can query a file's layers, components and tokens, generate code from a board, or create and modify elements. The MCP lets the model **execute arbitrary code inside the Penpot plugin**, so only connect files you're happy for Claude to edit, and keep version history on.

## Design to code with Claude

- Ask for one board or component at a time. Map Penpot tokens to Tailwind theme tokens, flex/grid layouts to the same CSS, and components to shadcn or project components.
- Check against the design visually (`browser-qa` screenshots), then apply `interface-polish`.

## Penpot vs Figma

Penpot is free with unlimited editors, open, self-hostable, and closer to CSS. Figma still leads on plugin ecosystem, Dev Mode, real-time performance on huge files, and FigJam. Clients deep in Figma may need you to stay there.
