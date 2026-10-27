---
name: editorial-themes
description: Build complete website themes in a quiet, editorial, premium style (typography-led, photo-led, square-cornered, restrained color, minimal motion), like the Lexington Astro themes. Use when Dean asks for a "theme", "template", "Lexington-style" or "editorial" site, a premium marketing site for a specific business type (law firm, agency, architect, restaurant, real estate, clinic, SaaS, portfolio, magazine…), or a multi-page site that should look like a high-end studio built it.
---

# Editorial themes

Build sites that feel designed by a small, opinionated studio: the type does the work, photography carries the mood, and everything else stays out of the way. This sits on top of `dean-design-taste` (stack, motion and maps defaults); where they differ, this skill wins for theme work.

**Originality rule:** this skill describes a style. Never copy Lexington's (or anyone's) code, copy text, theme names, logos or images. Write original copy and use licensed or placeholder imagery.

## 1. Brief (ask once, briefly, if not given)

- Business type and name, and what the site must sell or get people to do
- Light or dark
- Mood: pick a preset from [presets.md](presets.md), or describe one
- Pages needed (default set below)

## 2. Design language

### Typography is the design
- One neutral grotesk for everything (Switzer, General Sans, Inter, Geist), **or** a grotesk for UI plus an editorial serif for headlines (Newsreader, Instrument Serif, Fraunces). Never more than two families.
- Display headings are **big and quiet**: weight 400–500, never bold. Tight tracking (`-0.03em` to `-0.055em`) and tight leading (`0.86`–`1.0`). Hero sizes from `text-6xl` up to `clamp(4rem, 9vw, 8.5rem)`.
- Body is small and muted: 14–16px, `leading-relaxed`, mid-gray, max ~60ch.
- Labels and metadata are tiny (12–13px), often uppercase or with a muted color, never bold.
- Hierarchy comes from size, color and space, not weight.
- Optional voice tricks: a serif italic word inside a grotesk headline; the end of a paragraph fading to muted.

### Color
- Light: pure white or a barely warm off-white (`oklch(0.976 0.004 95)`), near-black text (`oklch(0.2 0.005 70)`), muted text around `oklch(0.5 0 0)`.
- Dark: soft near-black (`oklch(0.19 0.005 260)`), warm off-white text (`oklch(0.95 0.01 87)`), muted text around `oklch(0.7 0.008 87)`. Never pure `#000` on `#fff`.
- **At most one accent**, used for the primary CTA and little else (deep teal, oxblood, signal orange-red, forest green). Many themes have none.
- No gradients, no glows, no glassmorphism. Color comes from photography.
- Define tokens in OKLCH in Tailwind v4 `@theme` (or CSS variables), and pick light and dark values together.

### Shape and surface
- Square corners on content: images, cards, sections (`rounded-none`). Small radius (4–6px) only on UI chrome like buttons, inputs and the nav pill, if at all.
- No drop shadows. Separate things with whitespace, hairline borders (`border-black/10` / `border-white/10`) and background shifts.
- Buttons: small, solid, rectangular, short labels ("Book a consultation", "View work"). One primary per view.

### Layout
- Wide canvas: `max-w-7xl` or full width with 24–32px gutters. Generous vertical rhythm (`py-24`–`py-40` between sections).
- Asymmetric 12-column grids. Recurring patterns:
  - **Label column**: a tiny section label on the left (cols 1–3), content offset to the right (cols 4/5–12).
  - **Headline left, small paragraph right**, bottom- or top-aligned on a shared baseline.
  - **Split screen**: text on one half, full-bleed photo on the other (sticky on desktop).
  - **Metadata rows**: label/value pairs ("Studios / Since / Work", "Bedrooms / Area / Price").
  - **Indexed grids**: tiny `01` … `2025` above each card, uppercase caption below.
  - **Stat rows**: 4–6 big numbers with tiny labels ("20+", "98%", "€4.2M").
  - **Giant type moments**: one oversized word or line, sometimes as a slow marquee with inline thumbnails.
  - Full-bleed hero photo, with the headline below it rather than overlaid when the photo is busy.
- Nav: minimal, either a thin top bar (logo left, 4–6 links, one CTA right) or just logo + "Menu". Footer: large wordmark or a final statement, then small columns of links and contact details.

### Imagery
- Photo-led and full-bleed. One consistent grade per site (muted, natural, slightly desaturated, or B&W). People photographed candidly, not stock smiles.
- Consistent aspect ratios per grid (4:5 portraits, 3:2 landscapes, 1:1 products). Use `next/image` (or Astro `<Image>`) with `sizes`, plus blur or skeleton placeholders.
- Placeholders: neutral gray blocks with a caption of what goes there, or clearly licensed sources (Unsplash). Never hotlink from the reference site.

### Motion (sparse and slow)
- Hover: 150–300ms ease-out color/opacity changes, a subtle image scale (`1.02`–`1.04`) inside `overflow-hidden`, underline slide-ins.
- Scroll: fade/translate-up reveals (12–24px, 500–700ms, once), scroll-linked text that brightens word by word, slow marquees, sticky split-screen images.
- Page transitions: Astro View Transitions or a short Framer Motion fade. Nothing bouncy and nothing that delays reading.
- Respect `prefers-reduced-motion`: reveals become instant, marquees stop.

### Copy voice
- Plain, specific and confident. Short declarative sentences with concrete details ("Four chairs, one sink and no rush.", "Pay on every listing.").
- No buzzwords ("revolutionize", "seamless", "cutting-edge"), no exclamation marks, no emoji.
- Real content structure for the industry: listing facts, case-study results, practice areas, menus, rates. See [presets.md](presets.md).

## 3. Build

**Stack:** follow `dean-design-taste` (Next.js + TypeScript + Tailwind + Framer Motion) unless Dean asks otherwise. For a pure content/marketing site with no app logic, suggest **Astro + Tailwind v4** (content collections, near-zero JS), which is what this style is usually built in.

**Default page set** for a "theme":
Home · About/Studio · Services or Work (index + detail) · Journal/Blog (index + post) · Contact · 404 · Privacy/Terms. Add industry pages from the preset (Listings, Menu, Attorneys, Pricing, Docs…).

**Order:**
1. Tokens: fonts, color (light + dark), type scale, spacing, radius. Put them in `@theme` / CSS variables.
2. Primitives: `Container`, `Section` (with label column), `Grid`, `Heading` (display/section/label sizes), `Button`, `Link`, `Media` (aspect + placeholder), `Reveal` (motion wrapper with reduced-motion support).
3. Layout: header, footer, page shell.
4. Pages, in the order above. Put content in typed data files or content collections, not hard-coded in components, so the theme can be reskinned.
5. Responsive pass: on mobile, display type steps down with `clamp`, grids collapse to one column with the label above, and split screens stack with the image first.

## 4. Check before calling it done

- [ ] At most two font families; no bold display headings; tight tracking on large type
- [ ] At most one accent color; no gradients or shadows; content corners square
- [ ] Every section uses one of the layout patterns above, and the page doesn't read as "centered hero + 3 cards"
- [ ] Contrast meets WCAG AA, including muted text and text over photos
- [ ] Reduced motion respected; no layout shift from fonts or images
- [ ] Copy is original, specific and buzzword-free; nothing copied from the reference
- [ ] Lighthouse: performance and accessibility ≥ 95 on the home page
