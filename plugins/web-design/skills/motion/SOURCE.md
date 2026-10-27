# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/motion-foundations, motion-patterns, motion-advanced (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: "jeff" (ECC contributor)
- License: MIT (ECC repository license)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: merged three skills into one (core rules and tokens in SKILL.md; patterns and advanced code in references/); corrected the SSR claim (motion renders initial styles server-side; the real risk is hiding LCP content); relaxed the framer-motion ban to "prefer motion/react, never mix"; replaced indigo/white/gray example colors with theme tokens; removed cross-links to ECC skills.

## Notes

- Verdict: Dean's main animation reference; pairs with dean-design-taste's motion rules.
- Good at: shared duration/easing/spring tokens; reduced-motion handling; AnimatePresence/layout/layoutId rules; drag, swipe, reorder, text, SVG, useAnimate and loader patterns with cleanup.
- Weak at / risks: opinionated ("no inline numbers"); examples assume `@/lib/motion-tokens` exists, so create it first; some patterns (bouncy springs, cursor followers) are easy to overuse.
- Alternatives: Motion docs (motion.dev); bencho-blocks for ready-made interactions; CSS transitions for simple hovers.
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
