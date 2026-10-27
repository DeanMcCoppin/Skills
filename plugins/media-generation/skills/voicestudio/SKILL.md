---
name: voicestudio
description: Set up and use VoiceStudio, a free, fully local ElevenLabs alternative for text-to-speech, voice cloning, voice design, dubbing, transcription and audiobooks. Use when Dean needs a voiceover, narration, a cloned or designed voice, dubbing of a video, subtitles or transcripts, or asks about ElevenLabs, TTS, or "make this speak".
---

# VoiceStudio

[debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio) is a desktop app (Electron + Python backend) that runs speech models on Dean's own machine. There's no subscription and no per-character billing, and nothing leaves the machine unless a cloud option is turned on. The default engine is OmniVoice (646 languages), with whisper.cpp for transcription and optional engines such as CosyVoice.

## VoiceStudio or ElevenLabs?

- **VoiceStudio**: voiceovers for sites and videos, narration, drafts, transcription and subtitles, private audio, high volume. Free after setup.
- **ElevenLabs**: when the very top voice quality or emotional range matters more than cost (ads, flagship trailers), when there's no decent GPU or Apple Silicon machine, or when a hosted API is needed for a deployed app.

Full notes are in [SOURCE.md](SOURCE.md).

## Install (once per machine)

- **Preferred:** download the installer for the OS from [Releases](https://github.com/debpalash/VoiceStudio/releases/latest) (.dmg, .exe, .AppImage/.deb).
- The README's `curl … | sh` one-liner is a download-and-execute. If Dean wants it, fetch `scripts/install.sh` first and read it. At review it was https-only and checked SHA-256 of the release. Never run it unread.
- Hardware: Apple Silicon (Metal) or an NVIDIA GPU (CUDA) is recommended. CPU works but is slow, with ~5 GB disk for the small build. Intel Macs get the UI only.
- Models download through the in-app Model Manager. Ask before downloading large models.

## Use it from Claude Code

The backend listens on `http://localhost:3900` by default (honor Dean's setting if changed).
1. Check `GET /health`. If it's down, ask Dean to open the app. Don't install a second copy.
2. Discover what's actually installed: `GET /openapi.json`, then `GET /v1/audio/voices`. Never invent voice IDs.
3. Speech uses the OpenAI-compatible `POST /v1/audio/speech` (`model`, `voice`, `input`, `response_format`). Transcription uses `POST /v1/audio/transcriptions` (multipart `file`; `srt`/`vtt` for subtitles). OpenAI voice names there are aliases, so prefer a saved voice ID for consistent narration.
4. Check the HTTP status and probe the output file (e.g. `ffprobe`) before saying it worked. An error body can be saved as `speech.wav`.
5. An MCP endpoint is at `http://localhost:3900/mcp`, which can be added to Claude Code as an HTTP MCP server if Dean wants tool access instead of curl.
6. VoiceStudio publishes its own agent skill (`skills/voicestudio` in the repo, via `npx skills add debpalash/VoiceStudio`). It's AGPL-licensed, so it isn't copied here. Read it before installing it per project.

## For websites and videos

- Write the script for the ear: short sentences, numbers spelled the way they're said, punctuation for pauses. Generate per paragraph so retakes are cheap.
- Keep one saved voice per brand, and note its ID in the project's README.
- Export WAV masters and ship compressed files (AAC/MP3 at 128–192 kbps or Opus). Add captions (VTT) for accessibility.
- Dubbing: keep the original media, review segment timing before export, and keep music and effects unless Dean says otherwise.

## Don't

- Don't clone a voice without the speaker's permission, and don't make audio that impersonates real people deceptively.
- Don't switch to a cloud provider, enable remote backends or download models without asking.
- Check the selected model's own license before using outputs commercially. Weights are licensed separately from the app.
