# Rajnikant Raman — Personal Resume Site

Personal resume and portfolio site, hosted on GitHub Pages.

**Live:** [rajnikant7008.github.io](https://rajnikant7008.github.io)

## Stack

- Single-file HTML5 / CSS3 — no frameworks, no build step
- Inline SVG sprite ([Lucide](https://lucide.dev) + [Simple Icons](https://simpleicons.org)) — no icon font
- ~90 lines of vanilla JS for scroll spy and the contact form — no jQuery
- [Formspree](https://formspree.io) for contact form handling

Total page weight is roughly 75 KB plus a 5 KB avatar. There are no third-party
requests at runtime.

## Features

- Dark design with glass cards and gradient accents
- Fixed sidebar on desktop; collapses to a compact header with a horizontal nav strip on mobile
- Semantic heading outline (`h1` → `h2` → `h3`), skip link, labelled form fields, `aria-live` form status
- All text meets WCAG AA contrast (4.5:1) against its background
- Honours `prefers-reduced-motion`
- Print stylesheet — `Cmd+P` produces a clean light-on-white résumé
- SEO: Open Graph + Twitter large-image card, JSON-LD `Person` schema, canonical URL, `robots.txt`, `sitemap.xml`
- Custom `404.html`

## Layout

```
index.html              the entire site (markup, CSS, SVG sprite, JS)
404.html                custom not-found page
robots.txt              crawler directives + sitemap pointer
sitemap.xml             two URLs: home and the CV
rajnikant-resume.pdf    downloadable CV, linked from the sidebar
favicon.ico / .svg      RR monogram
apple-touch-icon.png    180x180 home-screen icon
images/
  profile.png           256x256 avatar (PNG fallback)
  profile.webp          256x256 avatar (WebP, served first)
  profile@2x.webp       512x512 avatar for retina
  og-card.jpg           1200x630 social share card
```

## Local Preview

Open `index.html` directly in a browser — all asset paths are relative, so
`file://` works with no server.

## Regenerating assets

The image and icon build scripts live one directory up, alongside the
full-resolution source photo (`profile-source-hires.png`):

```sh
python3 ../build_sprite.py    # re-downloads icons, writes /tmp/sprite.svg
python3 ../build_images.py    # regenerates avatar, OG card and favicons
```

`build_sprite.py` writes a standalone sprite; paste it back into `index.html`
in place of the existing `<svg style="display:none">` block.

## Updating the CV

Replace `rajnikant-resume.pdf` in the repo root. Keep the filename, it is
referenced by the sidebar button and by `sitemap.xml`.
