# WEB-NOTES.md

Web-usage notes for building the flat-HTML Sipelle site from this design system. This is the **only** file in `design-system/` that was not copied from upstream; everything else is a byte-for-byte port. Read this first, then `readme.md` (brand rules) and `spec-sheet.html` (visual spec).

## 1. Provenance

This folder is a verbatim copy made **2026-07-12** from `D:\GITHUB\sipelle\design\design_handoff_sipelle_app`. Every file here **except this `WEB-NOTES.md`** is byte-identical to its upstream original (SHA256-verified — all files pass).

**To change the design, edit upstream and re-copy. Never edit these copies in place** — local edits silently diverge from the source of truth and are lost on the next sync.

Two upstream items were intentionally skipped from the copy:

- the handoff-root `assets/` folder — an exact duplicate of `design-system/assets/` (already present here), not worth copying twice.
- `reference/Sipelle App.dc.html` — a proprietary-templating interactive prototype that does not stand alone. Read it upstream if you ever need it.

## 2. What's in this folder

- **`styles.css`** — the entry point; it `@import`s the four files in **`tokens/`**. The `tokens/` CSS is the single source of truth for every styling value (color, type, spacing, effects). Consume the custom properties; never hard-code the underlying values into pages.
- **`readme.md`** — the brand rules in prose: content voice, visual foundations, iconography, a per-file index, and the substitution caveats. Start here for how the brand should feel.
- **`reference/README.md`** — the full handoff spec: per-screen layouts and exact per-screen values. NOTE: its relative paths are written from the upstream handoff root, **not** from this folder, so don't follow them literally from here.
- **`reference/original-screens/`** — the three 768×1376 Stitch mockups (splash, home, results). Visual ground truth; the tokens were sampled from these.
- **`spec-sheet.html`** — a static visual spec of the tokens plus every component state. Open it in a browser to see the system rendered.
- **`assets/`** — 16 PNGs (wordmarks, illustrations, category chips, drink thumbnails, scan blob, wash/flourish swatches). See the substitution flags below regarding their painted backgrounds.
- **`components/core/`** — React reference **only**. This site is flat HTML, so **do not import the `.jsx`**. Instead read each component's `.prompt.md` (intent/usage) and `.d.ts` (props) and hand-write the HTML/CSS equivalent.
- **`SKILL.md`** — the upstream agent-skill entry for designing with this system (it points back at `readme.md`); not needed when building pages by hand.

## 3. Substitution flags (inherited from upstream)

These are upstream's stated approximations, carried over unchanged:

- **Fonts** are nearest-Google-Fonts guesses (Playfair Display for serif, Caveat for hand-written), loaded via a **network `@import`** in `tokens/typography.css` — the stylesheet reaches out to Google Fonts at runtime.
- **Icons** are Lucide stand-ins; the spec sheet **hotlinks the unpkg CDN**.
- **Artwork** is raster-cropped from the mockups and keeps a slice of the painted wash background — these are **not** transparent cut-outs.
- **No logo** exists beyond the two wordmark PNGs.

## 4. Phone-scale type warning

The px type scale in `tokens/typography.css` was authored for the **768px-wide @2x phone mockups**, so its values are phone-sized, not desktop-sized (for example, the greeting token is `72px`). **Do not consume these tokens raw on desktop pages** — remap or rescale them when building the site. `reference/README.md` lists the @1x per-screen values to work from.

## 5. Deliberately deferred

Not built yet — add only when a real page needs it, nothing speculative:

- responsive breakpoints and a `clamp()`-based fluid type scale.
- hover and focus-visible states — the system currently defines only a **press** state.
- self-hosting the fonts and icons (removing the runtime CDN dependencies noted above).
- transparent artwork cut-outs (background removal on the raster crops).
- whether `design-system/` should be excluded from the public Cloudflare Pages deploy.
