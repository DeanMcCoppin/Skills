# Source

- This skill: Dean (original), written with Claude. License: TODO (this repo has no LICENSE file yet).
- Context: ECC ships a `remotion-video-creation` skill with 29 rule files that appear to come from Remotion's official skills repo, https://github.com/remotion-dev/skills. That upstream has no LICENSE file, so the rule files were **not vendored** (unclear provenance). This skill points to the official skills instead, so they stay current.
- Reviewed: 2026-10-27 (ECC copy read; upstream README checked at 30d4553).

## Notes

- Verdict: the right tool for programmatic, on-brand videos (demos, promos, templated clips). Check Remotion's license for company use first.
- Good at: React-native video, deterministic frame-based animation, data-driven templates, captions, charts, server/Lambda rendering.
- Weak at / risks:
  - a company license is needed above 3 people
  - rendering is CPU-heavy
  - the API changes often, hence linking the official skills
  - the upstream skills repo has no license file
- Alternatives: Cap (screen recording plus editing); traditional editors (DaVinci Resolve, CapCut); open-higgsfield for AI-generated footage.
