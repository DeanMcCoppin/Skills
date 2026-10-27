---
name: yt-dlp
description: "Download, trim and convert online video and audio with yt-dlp (YouTube and 1,000+ sites) for legitimate uses: Dean's or a client's own videos to self-host on a site, audio or subtitles for transcription, Creative Commons or licensed footage, and offline reference. Use when Dean asks to download a video or audio, grab subtitles or a transcript, extract a clip or audio track, or mentions yt-dlp or youtube-dl."
metadata:
  pricing: free
  cost: "Free (public domain / Unlicense). Needs ffmpeg and a JS runtime (Deno) for full YouTube support."
  tags: [video, download, audio, subtitles, cli]
---

# yt-dlp

[yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp) is the maintained youtube-dl fork: a command-line downloader for YouTube and 1,000+ sites. It's released into the public domain.

## Rules: check these first

- **Only download what Dean has the right to use:** content Dean or the client owns, Creative Commons or otherwise licensed footage (keep the license and attribution), public-domain material, or personal offline viewing where that's legal. Downloading usually breaks YouTube's Terms of Service, and copyright still applies to the files.
- **Never** re-upload, embed or ship someone else's video on a site without permission. Stock or licensed footage, or `open-higgsfield` generations, are the alternatives.
- "YouTube Premium costs $14/month for this" isn't the same thing: Premium's offline downloads are licensed and in-app. yt-dlp is a different, unlicensed route.
- **Cookies:** `--cookies-from-browser` reads Dean's browser session cookies, which are credentials. Use it only when Dean asks, only for Dean's own account's private or members content, and never copy the cookies anywhere.

## Install

```bash
brew install yt-dlp ffmpeg deno          # macOS (or: pipx install "yt-dlp[default]")
yt-dlp -U                                # sites change constantly; update often
```

Full YouTube support needs a JavaScript runtime: Deno is preferred, and Node or Bun work too.

## Common commands

```bash
yt-dlp -F URL                                            # list formats
yt-dlp -f "bv*[height<=1080]+ba/b" --merge-output-format mp4 URL   # best ≤1080p as MP4
yt-dlp --download-sections "*00:01:10-00:01:25" URL      # just a clip
yt-dlp -x --audio-format mp3 URL                         # audio only
yt-dlp --write-subs --write-auto-subs --sub-langs en --skip-download URL   # subtitles only
yt-dlp -o "%(upload_date)s-%(title)s.%(ext)s" URL        # tidy filenames
```

## Using it on websites (own content only)

- Self-hosting Dean's or a client's own video is faster and more private than a YouTube embed. Re-encode for the web with ffmpeg: H.264 MP4 plus WebM, a muted loop for heroes, and a poster frame (see the `remotion` and `voicestudio` export notes).
- For transcripts, prefer subtitles (`--write-subs`). Otherwise extract the audio and transcribe it locally (OpenWhispr or VoiceStudio), then feed the text to `weknora` or Claude.
