<div align="center">

# Ugur Ersoz — Portfolio

Personal portfolio of **Ugur Ersoz** — a product developer and researcher in life-science engineering and digital health, based in Berlin.

[![Deploy](https://github.com/ugrersoz/my-portfolio/actions/workflows/deploy.yml/badge.svg)](https://github.com/ugrersoz/my-portfolio/actions/workflows/deploy.yml)
[![Pages](https://img.shields.io/website?url=https%3A%2F%2Fugrersoz.github.io%2Fmy-portfolio&label=live%20site&up_message=online&down_message=offline)](https://ugrersoz.github.io/my-portfolio)
[![License](https://img.shields.io/badge/license-dual--scope-blue.svg)](LICENSE)
[![Last Commit](https://img.shields.io/github/last-commit/ugrersoz/my-portfolio)](https://github.com/ugrersoz/my-portfolio/commits/main)

**Live → [ugrersoz.github.io/my-portfolio](https://ugrersoz.github.io/my-portfolio)**

</div>

---

## Overview

A minimal, Apple-inspired single-page portfolio presenting my background in life-science engineering, product development, and applied research. The site is fully static, dependency-free, mobile-first, and ships as a single self-contained HTML file deployed to GitHub Pages on every push to `main`.

### Highlights

- **Zero build step, zero runtime dependencies** — pure HTML5, CSS3, and vanilla JavaScript (66 LOC).
- **Single-page navigation** — section switching handled by a small client-side view toggle; no framework, no router library.
- **50 KB first load** — see [Performance](#performance) for the measurement and how it was achieved.
- **Mobile-first responsive layout** — hamburger menu, touch-friendly tap targets, breakpoints at 768 px / 480 px.
- **Accessible markup** — semantic landmarks, alt text on every image, keyboard-dismissable modal (`Esc`).
- **Continuous deployment** — pushes to `main` publish to GitHub Pages via GitHub Actions.
- **Deploy-time footer stamping** — the "last updated" date is injected into the published copy during deploy, so `main` is never modified by automation.

---

## Architecture

```
my-portfolio/
├── index.html                    # Single-page app: markup, styles, and scripts in one file
├── images/                       # Optimized WebP assets + icons (see Asset pipeline)
├── versions/                     # Frozen snapshots of earlier iterations (v0 … v7)
├── .github/
│   ├── workflows/deploy.yml      # Stamps footer date, then publishes to gh-pages
│   ├── ISSUE_TEMPLATE/           # Issue forms
│   └── pull_request_template.md
├── site.webmanifest              # PWA metadata
├── robots.txt · sitemap.xml      # Crawler directives
├── SECURITY.md                   # Vulnerability disclosure contact
├── LICENSE                       # Dual-scope: MIT for config, all rights reserved for content
└── README.md
```

| Layer       | Choice                                        | Rationale                                                     |
|-------------|-----------------------------------------------|---------------------------------------------------------------|
| Markup      | Semantic HTML5                                 | Accessibility, SEO, no framework lock-in                      |
| Styling     | Hand-written CSS3 (20 KB), system font stack   | No FOUT, no render-blocking external stylesheet               |
| Interaction | Vanilla JS (66 LOC)                            | Eliminates bundle, transpile, and supply-chain risk           |
| Images      | WebP, purpose-built derivatives                | See [Asset pipeline](#asset-pipeline)                         |
| Hosting     | GitHub Pages                                   | Free, fast, integrates natively with the repo's CI            |
| CI/CD       | GitHub Actions (`peaceiris/actions-gh-pages`)  | Declarative, auditable, no third-party deploy hook            |

---

## Performance

Measured on the committed source, not estimated.

| Metric                                   | Before   | After     | Change      |
|------------------------------------------|----------|-----------|-------------|
| **First load** (gzipped HTML + eager images) | 8.27 MB  | **49.8 KB** | −99.4 %     |
| Total image payload on disk              | 8.26 MB  | 1.0 MB    | −88 %       |
| Largest single asset                     | 6.58 MB  | 215 KB    | −97 %       |
| Deferred (lazy-loaded) images            | 0 KB     | 566 KB    | —           |

Targets tracked going forward:

| Metric                    | Target             |
|---------------------------|--------------------|
| Lighthouse Performance    | ≥ 95               |
| Lighthouse Accessibility  | ≥ 95               |
| First Contentful Paint    | < 1.0 s on 4G      |
| First load                | < 100 KB           |

---

## Asset pipeline

The single largest problem was one file: a 6.58 MB, 1760×2432 portrait that served **four** different roles — in-page avatar (rendered in a 160 px circle), favicon, apple-touch-icon, and Open Graph card. One oversized file cannot serve all four well, so it was split into purpose-built derivatives:

| Output                  | Size    | Format | Role                                    |
|-------------------------|---------|--------|-----------------------------------------|
| `profile.webp`          | 400²    | WebP   | In-page avatar (covers 2× displays)     |
| `favicon.png`           | 64²     | PNG    | Browser tab                             |
| `apple-touch-icon.png`  | 180²    | PNG    | iOS home screen                         |
| `icon-192/512.webp`     | 192²/512² | WebP | PWA manifest                            |
| `og-image.jpg`          | 1200²   | JPEG   | Social preview                          |

Decisions worth recording:

- **Center crop, not top crop.** The avatar renders with `object-fit: cover` in a 1:1 box, which is a center crop. The derivatives use the same crop so the rendered result is unchanged.
- **Lossy over lossless.** The portrait is a pixelated-style image, so lossless encoding was tested first on the assumption it would win. It did not — the image carries ~31 k distinct colours, making it a stylized photo rather than true low-palette pixel art. Lossless WebP measured 187 KB against 27 KB lossy at the same dimensions, so lossy was kept.
- **JPEG for `og:image`, WebP everywhere else.** Crawler support for WebP Open Graph images is still inconsistent across LinkedIn, X, and Facebook; the in-page assets have no such constraint.
- **`loading="lazy"` on off-screen images.** Every section except *Me* lives in a `display:none` container. Browsers still fetch `<img>` inside `display:none`, so all project and certificate images were previously downloaded on first paint. They are now deferred until the visitor navigates to that section — 566 KB moved off the critical path.

---

## Versioning

Frozen snapshots of earlier iterations live under [`versions/`](versions/) so the design evolution stays browsable. These predate a consistent tagging scheme; future releases will be marked with annotated Git tags following [Semantic Versioning](https://semver.org/).

---

## Roadmap

- [ ] Replace the `versions/` snapshots with annotated Git tags
- [ ] Lighthouse CI workflow with budget enforcement
- [ ] Dark-mode toggle that respects `prefers-color-scheme`
- [ ] Internationalisation (EN / TR / DE) via a small `data-i18n` shim
- [ ] Extend `aria-label` coverage across all interactive controls

---

## License & Usage

This repository is **public for transparency and reference only**.

- The deployment **workflow and config files** (`.github/workflows/`, `.gitignore`, `.editorconfig`, `robots.txt`, `sitemap.xml`, `site.webmanifest`) are released under the [MIT License](LICENSE).
- **All site content** — text, biography, project descriptions, photographs, certificates, HTML/CSS layout, and visual design — is **© Ugur Ersoz. All rights reserved.**

Cloning, redeploying, repurposing, or republishing this site (in whole or in part) as your own personal portfolio is **not permitted**. Re-use of any content requires prior written permission.

---

## Contact

**Ugur Ersoz** — Berlin, Germany
[Website](https://ugrersoz.github.io/my-portfolio) · [LinkedIn](https://www.linkedin.com/in/ersozugur) · [GitHub](https://github.com/ugrersoz) · uersoz55@gmail.com
