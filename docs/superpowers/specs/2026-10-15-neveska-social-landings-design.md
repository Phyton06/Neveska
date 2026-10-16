# Neveska Social Landing Pages

Create three complete, standalone mobile-first social landing pages for Neveska Martinez, using her supplied photos and preferred black color.
The project is published as a static site from the Git repository `github.com/Phyton06/Neveska` to GitHub Pages at `https://phyton06.github.io/Neveska/`; no application framework or build step is present.

## Approved design

Keep `noir-electrico.html`, retaining its electric-blue identity, adding inline vector brand marks for every social platform, shortening its copy, and adapting its layout for tablets and desktops. Keep and adapt `galeria-portada.html` and `galeria-rollo.html`. Remove `noir-editorial.html`, `noir-romantico.html`, and `galeria-mosaico.html`; do not delete or replace any other current page. Every retained page ends with a small credit line, `Desarrollado por Phyton`, where `Phyton` links to `https://phyton06.github.io/Portfolio/`.

Keep both existing gallery pages image-led, with each photo linking directly to its corresponding social platform:

- `galeria-portada.html` — one large photo-led cover with profile identity and social-photo links below.
- `galeria-rollo.html` — a contact-sheet / instant-photo gallery with a warmer blackroom aesthetic and lightly tilted frames, forming an always-filled 2×2 photo grid with the age-gated OnlyFans frame centered beneath both columns.

The user supplied the reference `https://sondra-blust.com/` and described the target as “mas como galeria y al clickear la foto sea el enlace a la red social”; the design borrows the broad image-led profile-and-gallery idea, not a pixel-for-pixel copy. Gallery photos remain clickable destinations, with a clearly visible platform icon and name in a high-contrast label. The electric page also displays recognizable social icons instead of text abbreviations, and every page uses the official OnlyFans brand mark. Keep user-facing copy to Neveska's name and `Sígueme en mis redes.`; the OnlyFans warning says only `Contenido +18`, alongside the existing age-confirmation and exit buttons. Desktop and tablet layouts use the available width and avoid empty gallery columns; mobile remains mobile-first. Use semantic HTML, keyboard-accessible controls, visible focus styles, adequate contrast, and reduced-motion-aware animation.

## Social links

Include Facebook, Instagram, TikTok, X, and OnlyFans. Since personal profile URLs are not yet available, use each platform's general homepage as a clearly temporary destination, opening external destinations in a new tab with safe `rel` attributes.

## OnlyFans age confirmation

Selecting OnlyFans opens an accessible confirmation dialog before navigation. The dialog contains the exact buttons `Tengo 18 años o más` and `Salir`. The confirmation button opens the general OnlyFans destination in a new tab; `Salir`, Escape, and clicking the backdrop close the dialog without navigation. The dialog must not claim to verify a visitor's actual age.

## Social sharing (Open Graph)

Each retained page exposes its own Open Graph and Twitter Card metadata so shared links render a complete, page-specific preview on every network. The deployment base is `https://phyton06.github.io/Neveska/` (repository `github.com/Phyton06/Neveska`), because Facebook and WhatsApp require absolute URLs. Every page declares `og:type`, `og:site_name`, `og:locale`, its own `og:title` (mirroring the page title), its own `og:description` (mirroring the page's meta description), its own absolute `og:url`, and its own absolute `og:image` pointing to a page-specific 1200×630 JPEG cropped from that page's signature photo: `og-noir-electrico.jpg` (blue portrait), `og-galeria-portada.jpg` (beach), and `og-galeria-rollo.jpg` (swing), each with `og:image:type`, `og:image:width`, `og:image:height`, and `og:image:alt`. The same values are mirrored in `twitter:card` (`summary_large_image`), `twitter:title`, `twitter:description`, `twitter:image`, and `twitter:image:alt`.

## Acceptance checks

1. `noir-electrico.html`, `galeria-portada.html`, and `galeria-rollo.html` load directly as standalone HTML without a build step; `galeria-mosaico.html` is absent.
2. The two gallery pages show all five supplied photos as clickable links, with the corresponding platform icon and legible name adjacent to each photo.
3. All three retained pages use concise copy, display the exact age notice `Contenido +18`, and render the official OnlyFans brand mark.
4. The electric page shows recognizable icons for Facebook, Instagram, TikTok, X, and OnlyFans.
5. Facebook, Instagram, TikTok, and X point to their public general homepages and open safely in a new tab.
6. OnlyFans never navigates before explicit confirmation; confirmation opens its general homepage, while exit dismisses the dialog.
7. Mobile, tablet, and desktop layouts use available space without horizontal overflow or empty gallery cells, and the roll gallery keeps equal photo frames with the OnlyFans frame centered beneath the two filled columns; keyboard and reduced-motion preferences remain supported.
8. Every retained page ends with the credit `Desarrollado por Phyton`, where `Phyton` links to `https://phyton06.github.io/Portfolio/`.
9. Every retained page carries its own Open Graph and Twitter Card metadata with absolute URLs based on `https://phyton06.github.io/Neveska/`, its own `og:url`, title, description, and a page-specific 1200×630 JPEG preview (`Imagenes/og-noir-electrico.jpg`, `og-galeria-portada.jpg`, `og-galeria-rollo.jpg`). The three pages and their preview images serve HTTP 200 from that base.

## Scope boundaries

Do not invent personal social handles or claim verified age. The implementation is limited to the three retained standalone pages; no framework, backend, or analytics is included. Publication is the static GitHub Pages site of the repository `github.com/Phyton06/Neveska`.
