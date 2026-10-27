# Video models and backends (scroll-world Step 4)

### Video model — pick ONE for the whole chain

**This skill only ships seamless output**, so the only usable models are ones that can
frame-lock a seam: every chained clip must accept `--start-image`, and connectors also
need `--end-image`. That capability — not preference — is the selection rule. Check any
model with `higgsfield model get <job_type>` and **skip anything whose media inputs are
reference-only** (no start/end image): it can only *condition* a generation, not
*continue* a shot, so it physically can't hold a seam. Schemas below were confirmed
against the CLI:

| Model | start/end image | Notes |
|---|---|---|
| `seedance_2_0` (default) | ✓ / ✓ | Full chain (legs + connectors). `--mode std --resolution 1080p`. Its NSFW filter is the touchy one (see Gotchas). |
| `kling3_0` | ✓ / ✓ | Full chain — tested: `--mode std --sound off --duration 5` with start+end images accepted, seams frame-lock cleanly. **No `--resolution` param** (don't pass one; `--mode std` returns **720p native** — encode what ffprobe reports, never upscale). Sound defaults **on** → `--sound off`. `--duration` default 5, try 10 for legs. Different content filter than Seedance — the sanctioned NSFW fallback. |
| `seedance_2_0_mini` | ✓ / ✓ | Cheap draft tier that keeps frame-locking (720p). The previz tier: run the whole chain here first, then re-render final legs on the full model — still seamless, so it translates directly. |

Those three are the roster — all do both architectures. (`kling3_0_turbo` also frame-locks
via `--start-image`, but has no `--end-image`, so it's architecture-A-only and can't make
connectors; it also takes a different flag set — no `--mode`, has `--resolution` — so it
doesn't drop into the pipeline as-is. It's not in the default roster; only reach for it, and
wire it by hand, if architecture A's sequential render time is a proven bottleneck and you've
benchmarked it as actually faster.)

One more architecture-A-only candidate, worth knowing because it is by far the cheapest
probe: **`minimax_hailuo`** (Hailuo-2.3, ~6 credits per 768p/6s clip vs 22–72 for the
roster). Verified 2026-07: `--start-image` + prompt frame-locks (output frame 0 ≡ input,
PSNR 33 dB) and a forward-glide prompt was obeyed, gently. Constraints: the 2.3 variant
rejects `end_image` (no connectors → arch A only), output aspect follows the input image
(hand it a 16:9 canvas, not a bare 3:2 still), motion runs subtler than seedance, and
don't pass `--resolution` (the CLI mis-types the enum; the 768 default works — 1080
supports 6s only). One clip ≠ a chain: qualify a leg-to-leg handoff before betting a
full build on it.

Rules:
- **One model for all chained clips.** Each renderer has its own motion/color/grain
  character; mixing models mid-chain keeps *position* continuity (frames still hand off)
  but the render-character shift reads as a subtle pop. The one sanctioned exception is
  the NSFW fallback for a single stubborn clip (Gotchas) — a slight character shift on
  one 5s connector beats a missing connector.
- Default to `seedance_2_0`, rendered through **Monid by default** (per-clip USD —
  next section) with Higgsfield credits as the fallback biller (Step 0.1/1.6); honor
  a user's stated preference **only if the model qualifies** (frame-locking). If it
  doesn't, say so and use a supported model — never ship a non-seamless build to
  satisfy a model request. `kling3_0` and `seedance_2_0_mini` exist only on the
  Higgsfield side.
- The pipeline scripts take the model as `$VMODEL` with per-model flags already cased
  out (`references/pipeline.md`).

### Monid backend — the DEFAULT chain biller (qualified 2026-07-25)

Monid's **`bytedance /v1/video/seedance-2.0`** passed both paid probes on
2026-07-25 and is the **default** way this skill renders the chain, for **both
architectures** — it is the roster's `seedance_2_0` served pay-per-USD (wiring in
pipeline.md → "Monid backend"; Higgsfield renders the chain only as the fallback
biller or for Higgsfield-only models):

- **Leg probe** (prompt + `first_frame` image): output frame 0 ≡ input still
  (PSNR 31.6 dB), forward-glide prompt obeyed, billed the advertised cell
  ($0.279 / 480p 4s).
- **Connector probe** (prompt + `first_frame` + `last_frame`): start locked
  (31.6 dB); the end **lands close but not pixel-perfect** (27.5 dB, same
  composition, prop-level drift) — the exact end-image behavior Seedance shows
  on Higgsfield, covered by the engine's seam crossfade and by using the next
  dive's ACTUAL first frame as the end-image (Step 5 law, unchanged).

The I/O contract differs from the Higgsfield CLI — three rules:

1. **Images go by URL, never inline.** `content` items are
   `{"type":"image_url","image_url":{"url":…},"role":"first_frame"|"last_frame"}`;
   base64 data URLs are **rejected** ("Must be a public https:// URL or an
   asset://<id> reference"). Local frames travel through Monid's free workspace
   file system: `sfs /put` → `curl -T` the bytes → `sfs /cat` returns a signed
   public URL to paste into the body ($0, explicitly built for this).
2. **Pass `ratio` explicitly** (`16:9`, or `9:16` for the mobile chain) — the
   adaptive default follows the input image's aspect instead.
3. **Bill-check every clip**: cost is token-priced
   (`w × h × 24 × sec / 1024` at $7–7.7/1M); read `cost.value` off each run.

History that shaped these rules (still true as of 2026-07-25): the seedance
endpoints were text-to-video-only until late July 2026 — **re-`inspect` before
each build; the catalog moves in both directions.** `minimax
/v1/video_generation` (Hailuo-2.3) remains disqualified: sending `prompt` +
`first_frame_image` together silently drops the image (unrelated t2v output,
wrong price cell); image-only frame-locks (33 dB) but has no camera control.

**Qualification protocol for any new/changed Monid endpoint** (each probe is one
cheap 480p clip): (1) prompt + first-frame from a real still — frame 0 must
match the input to codec noise (PSNR ≳ 30 dB) and `cost.value` must match the
advertised cell; (2) for connector duty, add a `last_frame` from a different
still — the end must land on that composition (Seedance-style near-miss is fine,
the crossfade covers it). Pass → pay-per-clip tier (arch A if start-only; full
roster if start+end).

