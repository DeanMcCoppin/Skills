# Source

- Tool: https://spline.design (commercial SaaS). React runtime: `@splinetool/react-spline`.
- This skill: Dean (original), written with Claude. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (pricing page). The embedding details are general Spline usage; check the current docs for the API.

## Notes

- Verdict: the fastest way to put real, interactive 3D on a marketing site without writing 3D code. Budget the Hobby plan for client work (no watermark), and always ship a mobile and low-power fallback.
- Cost reality:
  - Free exports carry the Spline logo; Hobby ~$12/month (yearly) removes it on 3D web exports.
  - Pro ~$25/month adds code export.
  - AI 3D generation needs a paid plan.
  - The promo's "free" is true only with the watermark.
- Good at: visual 3D design in the browser, states and events (hover, drag), easy React/Next.js embeds, runtime API to drive the scene from the page, AI 3D generation on paid plans.
- Weak at / risks:
  - heavy runtime and scene downloads (watch LCP)
  - touch-drag can fight page scroll
  - vendor-hosted scenes
  - commercial-use terms aren't spelled out on the pricing page
  - easy to make generic "glossy blob" visuals
- Alternatives:
  - React Three Fiber + drei (code, full control)
  - Three.js directly
  - Bencho pseudo-3D blocks
  - pre-rendered video (cheapest, no interactivity)
