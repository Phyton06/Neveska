# Neveska Social Landings Implementation Plan

> **For agentic workers:** Implement inline from the approved specification; keep all three retained pages independently usable.

**Goal:** Preserve and adapt the electric and two chosen gallery pages for clearer social navigation across mobile, tablet, and desktop.

**Architecture:** Each standalone root HTML file contains page-specific semantic markup, CSS, inline SVG brand marks, and age-dialog behavior without a build system. Gallery photos directly link to their platforms; the electric page retains its link-list structure with brand icons.

**Tech Stack:** HTML5, CSS, vanilla JavaScript; no dependencies or build step.

## Global Constraints

- Follow `docs/superpowers/specs/2026-10-15-neveska-social-landings-design.md`.
- Include the exact buttons `Tengo 18 años o más` and `Salir`.
- The retained pages are `noir-electrico.html`, `galeria-portada.html`, and `galeria-rollo.html`; remove only `galeria-mosaico.html` in this refinement.
- Gallery photos directly link to platforms with high-contrast brand icons and visible names; social-focused copy stays brief, including the `Contenido +18` notice.
- Use general platform homepages until personal profile URLs are supplied.
- Do not claim the dialog verifies actual age.
- Support narrow mobile widths, keyboard operation, visible focus, contrast, and reduced motion.
- Use the official OnlyFans brand mark on every page and end every page with the `Desarrollado por Phyton` credit linking to `https://phyton06.github.io/Portfolio/`.

---

## File Structure

- `noir-electrico.html` — retained electric-blue option, updated with actual brand icons.
- `galeria-portada.html` — full-bleed profile cover with vertical clickable photo gallery.
- `galeria-rollo.html` — staggered instant-photo/contact-sheet social gallery.
- Remove: `galeria-mosaico.html`.
- `Imagenes/*` — existing supplied photos; do not modify or duplicate these source images.

## Task 1: Adapt the retained social pages and remove the rejected mosaic

**Files:**
- Modify: `noir-electrico.html`
- Modify: `galeria-portada.html`
- Modify: `galeria-rollo.html`
- Delete: `galeria-mosaico.html`
- Test: built-in Python standard library `unittest` via a temporary script outside the repository.

**Interfaces:**
- Each page is independently opened directly in a browser and references existing relative image paths under `Imagenes/`.
- Each page exposes five named links and an OnlyFans confirmation dialog with confirm and cancel actions.

- [x] **Step 1: Verify updated acceptance checks fail before implementation**

Run the Python acceptance test and confirm it fails because the mosaic is still present, the retained copy is too long, desktop breakpoints are too narrow, and the roll gallery leaves a blank grid position.

- [x] **Step 2: Simplify copy and make `noir-electrico.html` responsive**

Keep the existing electric design and logos, show only the profile name plus `Sígueme en mis redes.`, reduce the age prompt to `Contenido +18`, and arrange the profile/photo and social links in a balanced desktop layout.

- [x] **Step 3: Simplify and adapt `galeria-portada.html`**

Keep the current photo-led cover, retain its social icon shortcuts and photo destinations, shorten copy to the name and `Sígueme en mis redes.`, use the brief age warning, and expand the gallery into columns on larger screens.

- [x] **Step 4: Fix `galeria-rollo.html` labels and desktop gallery flow**

Move each icon and social name to the high-contrast photo-frame caption strip; place the fourth photo in the unused left desktop slot; widen the page and gallery for tablet and desktop; use only the name and short social message; shorten the OnlyFans notice.

- [x] **Step 5: Remove only `galeria-mosaico.html`**

Delete the mosaic file only; retain the electric, portada, and rollo pages.

- [x] **Step 6: Run structural, responsive, and interaction checks**

Use the Python acceptance checks to verify exactly three retained pages, concise copy, readable labels, age gate, and layout rules. In a browser, check phone/tablet/desktop widths, legibility of all social names, column occupancy, and OnlyFans interactions; check reduced-motion handling. Observed: `python /tmp/opencode/test_neveska_refinement.py` passed (3 tests); browser checks at 320px, 768px, and 1280px loaded all photos with no horizontal overflow, and roll-gallery social labels fit. OnlyFans prompt, cancel, confirm, Escape, and backdrop behavior were exercised on all retained pages.

- [x] **Step 7: Report completion and limitations**

Summarize the three created files and check results. Note that profile URLs remain temporary general-homepage destinations and that this project directory is not a Git repository, so no commit can be created.

## Task 2: Final roll-gallery layout, OnlyFans mark, and developer credit

**Files:**
- Modify: `galeria-rollo.html`
- Modify: `noir-electrico.html`
- Modify: `galeria-portada.html`
- Test: temporary `unittest` script outside the repository; browser checks at 320/375/768/1280px.

- [x] **Step 1: Add failing acceptance checks for the three requested details**

Extend the temporary acceptance test to require the official OnlyFans glyph path (`M24 4.003h-4.015`), the `Desarrollado por` credit linking to `https://phyton06.github.io/Portfolio/` on every retained page, removal of the old `OF` text placeholder, and the roll-gallery arrangement `.frame:nth-child(4){grid-column:1;grid-row:2` / `.frame:nth-child(5){grid-column:1 / -1;grid-row:3` with `justify-self:center`. Observed: the updated suite failed 2 of 4 tests before the fixes.

- [x] **Step 2: Fix the roll-gallery middle gap and equalize photo frames**

Replace the leftover placements with explicit ones — Instagram/TikTok on row 1, X/Facebook on row 2, OnlyFans spanning both columns centered on row 3 — and give `.photo` `display:block` so its height applies; as an inline span it previously ignored heights, letting natural image ratios leave row gaps. Observed at 1280px: no empty cells, rows align within rotation skew (~6px), no horizontal overflow.

- [x] **Step 3: Replace the OnlyFans mark with the official logo on all pages**

Swap the `<text>OF</text>` placeholder for the official OnlyFans glyph path in all three inline SVG sprites and remove the dead text-font styling. Observed: the `#brand-onlyfans` symbol renders a non-zero path box on every page.

- [x] **Step 4: Add the developer credit to all pages**

Add `Desarrollado por <a href="https://phyton06.github.io/Portfolio/">Phyton</a>` as a centered bottom footer with per-page styling. Observed: visible and linked on all three pages.

- [x] **Step 5: Re-run checks**

Observed: `python /tmp/opencode/test_neveska_refinement.py` passed (4 tests). Browser checks at 320px and 768px showed no horizontal overflow, all images loaded, and the credit visible on all pages; the roll gallery was verified at 1280px (left column aligned, row 2 aligned, OnlyFans centered below both columns); the OnlyFans dialog blocked navigation until confirmed and Escape closed it without navigating.

## Task 3: Open Graph and Twitter Card previews

**Files:**
- Modify: `noir-electrico.html`, `galeria-portada.html`, `galeria-rollo.html` (head metadata only)
- Create: `Imagenes/og-neveska.jpg`
- Test: temporary `unittest` script outside the repository.

- [x] **Step 1: Add failing acceptance checks for social cards**

Extend the temporary acceptance test to require `og:type/site_name/locale/title/description/url/image` plus `twitter:card` (`summary_large_image`) and a 1200×630 JPEG preview image on all pages. Observed: the new subtest failed on all three pages before the metadata was added.

- [x] **Step 2: Create the 1200×630 preview image**

Crop the beach photo (`Imagenes/Captura desde 2026-10-15 17-33-25.png`, 638×905) to a 335px band centered at ~44% height, upscale with Lanczos, and save as `Imagenes/og-neveska.jpg`. Observed: 48,534 bytes; face-centered composition visually verified.

- [x] **Step 3: Add absolute social-card metadata to all three heads**

Insert the Open Graph and Twitter Card block after each page's title, mirroring the page's own title and using the confirmed base `https://phyton06.github.io/Neveska/` for `og:url` and `og:image` (user supplied the repository `github.com/Phyton06/Neveska`).

- [x] **Step 4: Re-run checks**

Observed: `python3 /tmp/opencode/test_neveska_refinement.py` passed (5 tests). A local `http.server` crawl returned the image as `200` `image/jpeg` (48,534 bytes) and all `og:*`/`twitter:*` tags on the served pages; real crawler previews require the deployed site.
