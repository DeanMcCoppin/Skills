# Source

- Tool: https://github.com/karpathy/autoresearch
- Author: Andrej Karpathy
- License: MIT
- This skill: Dean (original), written with Claude. No code copied. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 at 228791f (README, LICENSE).
- Filed under local-ai (AI on your own or rented hardware), since no category is about ML research.

## Notes

- Verdict: a great idea and a small, clean repo, but a research toy for Dean: it needs an H100-class NVIDIA GPU and runs agents with permissions disabled, so only use it in an isolated, rented GPU box.
- Good at:
  - a minimal, understandable loop (one editable file, one metric, a fixed time budget)
  - fun way to learn LLM training
  - the pattern transfers to other optimization tasks
- Weak at / risks:
  - needs an NVIDIA GPU (tested on H100), no real Mac/CPU path
  - GPU rental cost
  - the README says to run agents with all permissions disabled (isolate the environment)
  - not related to web work
- Alternatives: Running the pattern on cheaper metrics (Lighthouse, bundle size) locally; reading nanochat or nanoGPT to learn training
