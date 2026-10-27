---
name: rea-reverse-engineering
description: Use REA (Reverse Engineer Anything), an MCP server and CLI, to inspect and explain how software really behaves (Electron/JavaScript apps, native binaries, .NET, Android APKs, websites, network captures, firmware), with evidence. Use when Dean needs to debug or audit Dean's own app's build output, check what a dependency, SDK or third-party script actually does, investigate a suspicious package, analyze a site's network behavior, or asks to "reverse engineer" something Dean owns or is authorized to test.
---

# REA: reverse engineering with guardrails

[morluto/rea](https://github.com/morluto/rea) (MIT, npm package `rea-agents`) gives Claude MCP tools to inspect targets locally and return findings with evidence. It's powerful and high-trust, so the rules below come first.

## Rules (always)

1. **Authorization first.** Only analyze software, sites, devices or captures that Dean owns, builds, has a license allowing analysis, or has written permission to test. If the target is someone else's product, ask Dean to confirm authorization, and stop if it's unclear.
2. **No circumvention.** Don't bypass DRM, license checks, anti-cheat, authentication, bot protection or paywalls, even on request. Don't extract or reuse proprietary code or assets. "Learn how it works, then build our own version" means re-implementing the idea from scratch, never copying code.
3. **Static before runtime.** Start with static analysis. Runtime capture **runs the target with Dean's user permissions**, so ask before every runtime run, and run unknown or suspicious targets only in a VM or container.
4. **Report evidence, not guesses.** Cite the file, function, request or offset behind each finding, and mark anything inferred.
5. **Keep secrets out.** If analysis surfaces keys, tokens or personal data, don't print them in full; mask them and tell Dean where they were found.

## Setup: per project, no global config changes

Don't run `npx rea-agents setup`: it rewrites the config of every installed agent (Claude Code, Codex, Cursor…) and installs global instructions. Register it manually, pinned, only where it's needed:

```bash
claude mcp add rea --scope project -- npx -y rea-agents@6.8.0 mcp
```

This writes the project's `.mcp.json`; commit it only if the project should always have REA. Needs Node 22.23.4+ / 24.22.1+ / 26.12.1+. Before moving to a newer version, skim the changelog for new runtime or network behavior.

**Optional tools per target** (install only when needed and already licensed):
- native code: Ghidra (free), Hopper or IDA (commercial)
- Android: JADX and a JDK, plus adb for devices
- packet captures: tshark
- firmware: binwalk

REA can offer to install Hopper; decline unless Dean has decided to buy it.

## Good uses for Dean

- **Own apps:** inspect a production Next.js or Electron bundle to find what shipped (leaked env vars, dead code, oversized dependencies), or why a minified error happens.
- **Dependencies and SDKs:** check what an npm package, analytics script or chat widget actually does at runtime (network calls, storage, fingerprinting) before adding it to a client site. This pairs with the add-skill review checklist.
- **Suspicious packages:** static-only analysis of a package or binary flagged during a review, inside a container.
- **Network behavior:** analyze HAR files or captures from Dean's own sites to debug third-party calls and performance.
- **Interop:** understand a file format or local API of a tool Dean uses, to integrate with it legally.

## Output

A short report: the target and version, what was analyzed (static or runtime), findings with evidence, risks, and recommended actions. Save it next to the project's audit notes if Dean wants to keep it.
