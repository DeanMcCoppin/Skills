# Source

- Tool: https://github.com/OpenWhispr/openwhispr (OpenWhispr Team; MIT)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Not imported: the repo's `agent-skills/openwhispr-api` and `agent-skills/openwhispr-cli` (they target the API/MCP, which needs the Pro plan). Revisit if Dean subscribes.
- Reviewed: 2026-10-27 (README, LICENSE, pricing page). The app code wasn't audited.

## Notes

- Verdict: a real, free replacement for Wispr Flow for daily dictation. Run local models on the free plan; Pro is only for convenience (hosted cloud, sync, mobile).
- Cost reality: local dictation is unlimited and free on every plan. Pro is $80/year, Business $160/year. The promo's "$200/mo saved" is inflated: Wispr Flow is about $12–15/mo per person (not verified today).
- Why it's credible: MIT, ~10k stars, ~2,500 commits, a Homebrew cask, a security policy, "no telemetry" stated in the README.
- Good at:
  - hotkey dictation into any app
  - fully offline Whisper/Parakeet with GPU acceleration
  - custom dictionary, 100+ languages
  - local meeting transcription with speaker identification
  - notes with semantic search
  - a voice assistant using your own model keys (including Claude)
  - Mac, Windows and Linux
- Weak at / risks:
  - auto-paste needs Accessibility permission on macOS (broad access, as with any dictation app)
  - Electron app, so heavier than native
  - Intel Macs have limits (speaker identification)
  - many open issues and PRs (~220 each), so expect rough edges
  - the cloud tier is run by them (Neon Postgres), so stay local for privacy
  - the Homebrew cask is community-maintained
- Alternatives:
  - Wispr Flow (polished, paid)
  - macOS built-in Dictation (free, weaker)
  - Superwhisper / MacWhisper (paid native Mac apps)
  - VoiceStudio's dictation (fine, but OpenWhispr is the better daily driver)
- Overlap: voicestudio covers voice *generation*; this covers voice *input*. Keep both.
