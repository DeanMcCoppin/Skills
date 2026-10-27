# Budget and tiers (scroll-world Step 1.7)

Prices observed by the original author in July 2026; re-check live pricing (`monid inspect`, Higgsfield balance diff) before every build.

7. **Budget — engines shown by cost, decided before anything renders.** Present the
   render tiers (`AskUserQuestion`), then compute and state the estimated total for
   the user's N scenes — `N stills + (2N−1) videos [videos ×2 if mobile] + ~15%
   re-roll headroom` — and get a go before generating.
   - **Video tier** (roster only — every option frame-locks seams, Step 4):

     | Tier | Model | Rough cost |
     |---|---|---|
     | Draft / previz | `seedance_2_0_mini` (720p) | ~¼ of Standard |
     | Standard (default) | `seedance_2_0` (1080p) | baseline |
     | Alternate | `kling3_0` (720p native) | ≈ Standard; different look + content filter |

     Draft doubles as the previz path: run the whole chain cheap, approve the
     journey, re-render final legs on Standard (pipeline.md Notes) — suggest it
     unprompted when the balance reads tight.
   - **Backend — Monid is the DEFAULT biller for the chain** (Step 0.1; wiring
     in pipeline.md → Monid backend). Same Seedance 2.0, per-clip USD instead of
     credits. Token-priced `width × height × 24 × seconds / 1024` at $7/1M
     (480p/720p) or $7.7/1M (1080p) — measured: 1080p 8s dive ≈ $2.99, 5s
     connector ≈ $1.87; 720p ≈ $1.21 / $0.76; 480p ≈ $0.28 / $0.35. An N=6
     desktop chain ≈ $27 at 1080p / ~$11 at 720p vs Higgsfield Plus-monthly ≈
     $32 / $16 — ~15% cheaper per clip, parity with Plus-annual; structurally
     better for one-off builds (pay-per-use, no monthly expiry). On Monid the
     Draft/previz tier is simply the **same endpoint at 480p** — no model swap,
     so previz→final stays one-model by construction. State `monid balance`
     against the estimate; **fall back to Higgsfield credits** (per-model tiers
     above) when the user prefers their subscription, the balance is short, or
     the model must be `kling3_0` (Higgsfield-only). It's the same underlying
     model (`seedance_2_0` ≙ Monid's `seedance-2.0`), so finishing a stranded
     chain on the other biller is a reasonable rescue — but the serving stacks
     differ and cross-provider seam character is **untested**: eyeball the first
     rescued seam before rendering the rest, same as any model swap.
   - **Stills source** (only offer if the Codex CLI is present, Step 0.5):
     Higgsfield `gpt_image_2` (spends credits) vs **Codex `image_gen`** — the same
     gpt-image-2 model billed to the ChatGPT subscription (zero credits; counts
     toward Codex usage limits; 1536×1024 output — exactly 3:2, slightly under
     Higgsfield's 2k). Stills are plain PNGs handed to `--start-image`, so the
     video chain is indifferent to their source. Command in Step 2. **One source
     for all N stills of a build** — the two render with slightly different
     character (verified: Codex runs warmer/lighter), and mixing sources across
     scenes reads as style drift, same reason the video chain uses one model.
   - **Calibrate costs, don't guess.** The CLI exposes no pricing and plans differ.
     Run ONE still and ONE video first, diff `higgsfield workspace list` before/
     after, extrapolate to the full run, and warn the user whenever the estimate
     exceeds ~70% of the balance. (Observed on a plus plan, 2026-07: Standard
     video ≈ 40–55 credits, still ≈ 15.) A real `not_enough_credits` mid-run is
     recoverable (finished clips survive; resume after top-up) but ugly — the
     whole point of this step is that the user decides *before* the spend.

