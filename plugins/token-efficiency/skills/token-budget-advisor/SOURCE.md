# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/token-budget-advisor (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: Xabier Ariznabarreta Alomar (original TBA project, MIT), adapted by ECC
- License: MIT (upstream TBA and ECC)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: removed the invented "85-90% accuracy" figure and the dependency on ECC's context-budget skill; restricted it to explicit requests; description rewritten.
- Upstream: https://github.com/Xabilimon1/Token-Budget-Advisor-Claude-Code- (MIT).

## Notes

- Verdict: handy when Dean wants control over answer length; otherwise stays out of the way.
- Good at: clear depth levels and shortcuts ("tldr", "50%"); remembers the chosen level for the session.
- Weak at / risks: estimates are rough heuristics; the menu costs a round-trip, so only use it on request.
- Alternatives: just asking for "short" or "detailed" directly.
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
