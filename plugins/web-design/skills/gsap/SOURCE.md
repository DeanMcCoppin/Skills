# Source

- Tool: https://gsap.com (GreenSock, owned by Webflow). License: Standard "No Charge" GSAP License (free including commercial use and all plugins; **not** open source).
- This skill: Dean (original), written with Claude. React guidance is from gsap.com/resources/React. License: TODO (this repo has no LICENSE file yet).
- Reviewed: 2026-10-27 (licensing page and FAQ, React guide).

## Notes

- Verdict: the industry standard for scroll storytelling and timeline choreography, now fully free. Use it alongside `motion`, not instead of it: Motion for React UI state, GSAP for sequenced and scroll-driven work and non-React pages.
- License facts:
  - free for commercial use, with every former Club plugin included (SplitText, MorphSVG and the rest)
  - proprietary: Webflow owns it and can amend the terms
  - you can't build no-code visual animation tools that compete with Webflow, and you can't remove notices
  - AI-generated code is explicitly allowed
- Good at: ScrollTrigger (pin/scrub), timelines, SplitText, SVG morph/draw, Flip, matchMedia breakpoints, framework-agnostic, very performant.
- Weak at / risks: easy to overdo scroll-jacking and pinning (bad on mobile and for accessibility); imperative style in React needs useGSAP discipline; it's a proprietary license controlled by Webflow.
- Alternatives:
  - `motion` (React UI animation)
  - CSS scroll-driven animations (native, limited)
  - Lenis (smooth scroll only)
  - anime.js (MIT, smaller)
