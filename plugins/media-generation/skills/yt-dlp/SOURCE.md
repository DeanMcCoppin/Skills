# Source

- Tool: https://github.com/yt-dlp/yt-dlp
- Author: yt-dlp contributors
- License: Unlicense (public domain); yt-dlp-ejs Unlicense
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (LICENSE, README dependency and option sections; latest tag 2026.10.26).

## Notes

- Verdict: the standard tool for downloading web video; legal use only (own, licensed or CC content).
- Good at:
  - 1,000+ sites
  - format selection
  - clip sections
  - audio extraction
  - subtitles
  - SponsorBlock
  - frequent releases
- Weak at / risks:
  - using it on others' content breaks most sites' ToS and can infringe copyright
  - sites break often (keep it updated)
  - YouTube needs a JS runtime plus yt-dlp-ejs
  - `--cookies-from-browser` touches session credentials
- Alternatives: YouTube Premium offline (licensed, in-app only); creator-provided downloads; stock footage libraries; the promo's "$14/month" comparison is apples to oranges
