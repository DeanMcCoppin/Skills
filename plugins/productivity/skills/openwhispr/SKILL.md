---
name: openwhispr
description: "Set up and use OpenWhispr, the free open-source Wispr Flow alternative for hotkey voice dictation (local Whisper/Parakeet), meeting transcription and notes. Use when Dean wants to dictate instead of type (including prompts into Claude Code), set up voice typing or meeting notes, compares Wispr Flow or Granola, or has trouble with OpenWhispr hotkeys, models or permissions."
metadata:
  pricing: freemium
  cost: "Local dictation free and unlimited; Pro $80/yr only for hosted cloud, sync and mobile."
  tags: [dictation, speech-to-text, meetings, local-ai]
---

# OpenWhispr

[OpenWhispr/openwhispr](https://github.com/OpenWhispr/openwhispr) (MIT) is an Electron desktop app for macOS, Windows and Linux. Press a hotkey, speak, and the text is pasted at the cursor in any app. It also does meeting transcription with local speaker labels, notes with semantic search, and an AI voice assistant.

## Pick the setup

- **Default for Dean: free plan, local models.** Unlimited and private: audio never leaves the machine. Use Whisper (whisper.cpp, GPU on Metal/CUDA/Vulkan) or NVIDIA Parakeet. Parakeet is fast for English; Whisper is better for many languages.
- **Bring your own API key** for cloud transcription or AI cleanup (OpenAI, Groq, Anthropic, Gemini, OpenRouter): unlimited on the free plan, billed by that provider. Dean's Claude subscription doesn't cover API use.
- **OpenWhispr Cloud (Pro, $80/year)** only if Dean wants their hosted transcription without bringing API keys, cross-device sync, the iPhone app, agent mode, or their API/MCP. The free plan includes 2,000 cloud words/week. Prices are as of 2026-10-27; check openwhispr.com/pricing.

## Install

- macOS: `brew install --cask openwhispr` (community-maintained cask), or the `.dmg` from [Releases](https://github.com/OpenWhispr/openwhispr/releases).
- Windows: `.exe` from Releases. Linux: AppImage, `.deb`, `.rpm` or `.tar.gz` from Releases.
- On first run, grant the **microphone** permission and, on macOS, **Accessibility** (needed for auto-paste at the cursor). If text isn't pasting, Accessibility is the usual cause; see the repo's `TROUBLESHOOTING.md`.
- Download a local model in settings (start with a small or base model; go bigger if accuracy is poor and the machine is fast).

## Dictating into Claude Code

- Use it for long prompts, explaining bugs, describing designs, and reviewing feedback. Speaking is much faster than typing long text.
- Add a custom dictionary of project words (framework names, component names, client names) so they transcribe correctly.
- Speak the structure: "first… second…", "new line", and file names spelled out when they're unusual. Glance over the text before sending, because homophones in code terms slip through.
- Keep AI cleanup **off** or light for prompts: Claude handles raw speech fine, and cleanup can change technical meaning.
- Don't dictate secrets (API keys, passwords). They end up in the transcript history.

## Meetings and notes

- Meeting transcription runs locally with speaker labels. Get consent from everyone before recording, as the law requires in many places.
- Turn transcripts into tasks or briefs by pasting them into Claude, or use OpenWhispr's AI actions.

## Not this tool

- For generating voiceovers, cloning voices or dubbing, use **voicestudio** (media-generation plugin). OpenWhispr is for input, VoiceStudio is for output.
