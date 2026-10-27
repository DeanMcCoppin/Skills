# Source

- Tool: https://github.com/CapSoftware/Cap (Cap Software; AGPLv3 by default, MIT for `cap-camera*` and `scap-*` crates)
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (GitHub page, cap.so pricing). Self-hosting steps weren't tested; follow the repo's self-hosting docs.

## Notes

- Verdict: a polished, credible Loom replacement, with the best local editor (Studio mode) of the lot. But it isn't free for client work: the free plan is personal-use only.
- Cost reality:
  - The free plan is personal use only.
  - Commercial use needs the Desktop License: $29/year or $58 once.
  - Pro is $12/month (~$8.16 billed yearly) for unlimited cloud and AI.
  - Self-hosting the share server is free, using your own storage.
  - The promo's "$18/mo saved" assumes a Loom Business seat. Realistically Dean pays $58 once, or about $98/year for Pro.
- Why it's credible: ~24k stars, ~12k commits, an active company with bounties on Algora, a Rust/Tauri native app, S3-compatible storage support.
- Good at:
  - instant share links
  - Studio editor (auto-zoom, backgrounds, captions), 4K/60 export
  - local-only recording
  - bring-your-own S3 or Google Drive
  - viewer analytics and comments
  - Loom import
  - macOS and Windows
- Weak at / risks:
  - personal-use-only free tier
  - AGPL if you modify and host it for others
  - no Linux desktop app
  - viewer analytics use Tinybird, so check privacy needs
  - ~200 open issues
- Alternatives:
  - Loom (polished, pricier)
  - OBS (free, no instant links, more setup)
  - Screen Studio (Mac, paid, great demo videos)
  - macOS built-in screen recording (free, basic)
