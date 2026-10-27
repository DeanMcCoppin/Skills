# Source

- Source: https://github.com/affaan-m/ECC/tree/main/skills/accessibility + frontend-a11y (ECC, "Everything Claude Code", by Affaan Mustafa and contributors)
- Author: ECC maintainers (accessibility); community (frontend-a11y)
- License: MIT (ECC repository license)
- Imported: 2026-10-27 at commit 25278e7 (2026-10-26, release 2.2.3). Every file was read in full; nothing was executed.
- Changes: merged two skills: a web-only WCAG 2.2 AA SKILL.md (iOS/Android mapping dropped) plus references/react-patterns.md; fixed SC numbers (visible focus is 2.4.7; 2.4.11 is Focus Not Obscured); replaced the hand-rolled combobox dropdown with guidance to use native elements or Radix/React Aria; recommended native <dialog>; added an automated + manual audit section (jsx-a11y, axe, keyboard, screen reader).

## Notes

- Verdict: the a11y baseline for all of Dean's React/Next work; use the checklist on every interactive component.
- Good at: forms and errors, ARIA usage, live regions, focus restoration, images, reduced motion; WCAG 2.2 criteria with numbers.
- Weak at / risks: automated checks only catch part of it; still needs manual screen-reader passes.
- Alternatives: WAI-ARIA APG; Radix / React Aria docs; Deque axe.
- Review: when re-syncing from ECC, diff against the commit above and re-apply the changes listed.
