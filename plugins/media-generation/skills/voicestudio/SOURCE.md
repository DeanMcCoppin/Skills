# Source

- Tool: https://github.com/debpalash/VoiceStudio (authors: Palash Debnath, Shimul Debnath, plus contributors)
- Tool license: AGPL-3.0 for the app; model weights, voices and generated-output terms are licensed separately (see the repo's LICENSE-NOTICE.md).
- This skill: Dean (original), written with Claude. No code or text copied from VoiceStudio; API facts (port, endpoints) are taken from its docs. License: TODO (this repo has no LICENSE file yet).
- Not imported: the repo's own `skills/voicestudio/SKILL.md` (AGPL; not permissive, per the add-skill rules). It reviewed clean and is well written, so it's fine to install per project with `npx skills add debpalash/VoiceStudio` if wanted.
- Reviewed: 2026-10-27 (README, `skills/voicestudio/SKILL.md`, `scripts/install.sh`).

## Notes

- Verdict: a real ElevenLabs replacement for most day-to-day work (voiceovers, narration, transcription, subtitles, dubbing drafts), free and private. Keep ElevenLabs only for top-tier quality or hosted API needs.
- Why it's credible: ~78–90k stars with ~6,000 commits, a named core team, CI, releases for every OS, docs, an API and MCP server. Unlike Open Higgsfield, it actually runs the models locally.
- Savings: the "$22/mo" in the promo matches a mid-tier ElevenLabs plan; the real saving depends on usage, and ElevenLabs pricing wasn't verified here.
- Good at:
  - fully local, no per-character cost
  - 646 languages
  - cloning and voice design from a description
  - dubbing, dictation, audiobooks
  - OpenAI-compatible REST API, MCP endpoint, watch folders and recipes for automation
- Weak at / risks:
  - voice quality and emotional range may trail ElevenLabs' best voices
  - slow without Apple Silicon or an NVIDIA GPU
  - big install and model downloads
  - AGPL: personal use and using the outputs are fine, but if Dean modifies it and offers it as a network service, the source must be shared
  - each model's own license can restrict commercial use of outputs
  - the official one-liner is `curl | sh` (the script itself looked careful)
  - usage analytics are opt-in (consent)
- Alternatives: ElevenLabs (hosted, best quality, paid); OpenAI TTS API (cheap hosted, no cloning); other local TTS models run directly (more setup, no studio).
- Overlap: openwhispr (productivity) is the better daily dictation tool; this skill focuses on voice output.
- Review: re-read `scripts/install.sh` and the analytics settings on major updates.
