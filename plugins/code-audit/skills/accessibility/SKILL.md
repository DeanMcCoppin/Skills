---
name: accessibility
description: "Build and audit accessible web UI to WCAG 2.2 AA in React/Next.js - semantic HTML, labels and form errors, ARIA (only when needed), keyboard navigation, focus management, contrast, target size, reduced motion, screen-reader support. Use when building or reviewing forms, modals, menus, tabs or other interactive components, fixing a11y lint or review findings, or auditing a page before launch."
metadata:
  pricing: free
  cost: "Free: guidance. Tools used (axe, jsx-a11y) are free."
  tags: [a11y, wcag, react, forms]
---

# Accessibility (WCAG 2.2 AA)

Interfaces must be **Perceivable, Operable, Understandable and Robust** for keyboard, screen-reader, switch and zoom users. React patterns with code (forms, ARIA, live regions, focus, images, reduced motion) are in [references/react-patterns.md](references/react-patterns.md).

## How to build it in

1. **Pick the native element first:** `<button>`, `<a href>`, `<label>`, `<select>`, `<dialog>`, headings in order. ARIA is a last resort, and wrong ARIA is worse than none.
2. **Perceivable:** text contrast at least **4.5:1** (3:1 for large text and UI parts), text alternatives for meaningful images and icons (`alt=""` for decorative ones), reflow up to 400% zoom with no loss of function, and never color alone to convey meaning.
3. **Operable:** everything reachable and usable by keyboard with a **visible focus indicator** (SC 2.4.7) that isn't hidden behind sticky headers or overlays (SC 2.4.11, Focus Not Obscured). Targets at least **24×24 CSS px** (SC 2.5.8; aim for 44×44 on touch). A single-pointer alternative to any drag (SC 2.5.7). No positive `tabIndex`.
4. **Understandable:** consistent navigation, labels connected to inputs, specific error messages with suggestions (SC 3.3.3), no asking for the same data twice (SC 3.3.7 Redundant Entry), and accessible authentication without puzzles (SC 3.3.8).
5. **Robust:** correct name, role and value; `aria-live` / `role="status"` for dynamic updates; dialogs contain focus, close on Escape and return focus to the trigger.

## Audit

- **Automated:** `eslint-plugin-jsx-a11y` in the editor and CI, and **axe-core** (`@axe-core/playwright` in E2E, or browser extensions). Automated tools catch only about 30–40% of issues: a clean run is necessary, not sufficient.
- **Manual:** keyboard-only pass (Tab, Shift+Tab, Enter, Space, Escape, arrows), screen reader spot check (VoiceOver or NVDA) on key flows, 200% and 400% zoom, `prefers-reduced-motion` on, and Windows high-contrast / forced colors.
- Report: issue, WCAG criterion, `file:line` or selector, severity, fix.

## Checklist

- [ ] Every input has a connected `<label>`; errors are linked with `aria-describedby`, marked `aria-invalid` and announced
- [ ] No `onClick` on `<div>`/`<span>`; icon-only buttons have an accessible name; decorative icons are `aria-hidden`
- [ ] Headings are sequential; landmarks (`header`, `nav`, `main`, `footer`) are present; a skip link on content-heavy sites
- [ ] Focus is visible, never obscured, logically ordered, and restored after dialogs and menus close
- [ ] Contrast passes in light **and** dark mode, including placeholder, disabled and muted text
- [ ] Targets are at least 24×24 px; drag has a click alternative
- [ ] Dynamic content uses live regions; route changes move focus or announce the new page
- [ ] Animations respect `prefers-reduced-motion`; nothing flashes more than 3 times per second
- [ ] Menus, selects, tabs and dialogs come from native elements or Radix / React Aria

## Anti-patterns

- Div-buttons, placeholder-as-label, `aria-label` on elements with no role, `aria-hidden` on focusable elements.
- Color-only status (a red border with no text).
- Alt text like "image of…" (screen readers already say "image").
- Modals that let focus escape into the page behind, or that can't be closed by keyboard.

## References

- [WCAG 2.2](https://www.w3.org/TR/WCAG22/) · [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/) · [web.dev Learn Accessibility](https://web.dev/learn/accessibility/)
