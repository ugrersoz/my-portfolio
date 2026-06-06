<div align="center">

# Ugur Ersoz — Portfolio

Personal portfolio of **Ugur Ersoz** — a product developer and researcher in life-science engineering and digital health, based in Berlin.

[![Deploy](https://github.com/ugrersoz/my-portfolio/actions/workflows/deploy.yml/badge.svg)](https://github.com/ugrersoz/my-portfolio/actions/workflows/deploy.yml)
[![Pages](https://img.shields.io/website?url=https%3A%2F%2Fugrersoz.github.io%2Fmy-portfolio&label=live%20site&up_message=online&down_message=offline)](https://ugrersoz.github.io/my-portfolio)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Last Commit](https://img.shields.io/github/last-commit/ugrersoz/my-portfolio)](https://github.com/ugrersoz/my-portfolio/commits/main)
[![Code Size](https://img.shields.io/github/languages/code-size/ugrersoz/my-portfolio)](https://github.com/ugrersoz/my-portfolio)

**Live → [ugrersoz.github.io/my-portfolio](https://ugrersoz.github.io/my-portfolio)**

</div>

---

## Overview

A minimal, Apple-inspired single-page portfolio presenting my background in life-science engineering, product development, and applied research. The site is fully static, dependency-free, mobile-first, and ships as a single self-contained HTML file deployed to GitHub Pages on every push to `main`.

### Highlights

- **Zero build step, zero runtime dependencies** — pure HTML5, CSS3, and vanilla JavaScript.
- **Single-page navigation** — section switching driven by a lightweight client-side router (no framework, no router library).
- **Mobile-first responsive layout** — hamburger menu, touch-friendly tap targets, and breakpoints at 768 px / 480 px.
- **Accessible by default** — semantic landmarks, `aria-label`s on interactive controls, alt text on all images, and keyboard-navigable modals.
- **Continuous deployment** — pushes to `main` are published to GitHub Pages within ~30 seconds via a tagged GitHub Actions workflow.
- **Automated README metadata** — last-commit date and latest tag are synced into this README on every push.

---

## Architecture

```
my-portfolio/
├── index.html              # Single-page app: markup, styles, and scripts in one file
├── images/                 # Profile photo, project visuals, certificates
├── versions/               # Frozen historical snapshots (v0 … v7)
├── .github/
│   └── workflows/
│       ├── deploy.yml          # GitHub Pages publish on push to main
│       └── update-readme.yml   # Auto-sync version + last-commit date in README
├── LICENSE                 # MIT
└── README.md
```

| Layer        | Choice                                          | Rationale                                                                 |
|--------------|-------------------------------------------------|---------------------------------------------------------------------------|
| Markup       | Semantic HTML5                                  | Accessibility, SEO, no framework lock-in                                  |
| Styling      | Hand-written CSS3, system font stack            | Sub-50 KB CSS, no FOUT, instant first paint                               |
| Interaction  | Vanilla JS (~150 LOC)                           | Eliminates bundle, transpile, and supply-chain risk                       |
| Hosting      | GitHub Pages                                    | Free, fast, integrates natively with the repo's CI                        |
| CI/CD        | GitHub Actions (`peaceiris/actions-gh-pages`)   | Declarative, auditable, no third-party deploy hook                        |

---

## Performance & Quality Targets

| Metric                    | Target            |
|---------------------------|-------------------|
| Lighthouse Performance    | ≥ 95              |
| Lighthouse Accessibility  | ≥ 95              |
| Lighthouse Best Practices | ≥ 95              |
| First Contentful Paint    | < 1.0 s on 4G     |
| Total Page Weight         | < 500 KB (gzipped)|

The single-file design avoids render-blocking external CSS/JS; only image assets are fetched after the initial response.

---

## Versioning

The project uses [Semantic Versioning](https://semver.org/). Frozen snapshots of each major iteration live under [`versions/`](versions/) so the design evolution stays browsable. The version badge above is sourced from the latest annotated Git tag.

---

## Roadmap

- [ ] Lighthouse CI workflow with budget enforcement
- [ ] Dark-mode toggle that respects `prefers-color-scheme`
- [ ] Internationalisation (EN / TR / DE) via a small `data-i18n` shim
- [ ] Pre-compressed Brotli assets served from `gh-pages` branch
- [ ] Web Vitals telemetry (Beacon API → Cloudflare Worker)

---

## License & Usage

This repository is **public for transparency and reference only**.

- The deployment **workflow files** (`.github/workflows/`) are released under the [MIT License](LICENSE).
- **All site content** — text, biography, project descriptions, photographs, certificates, HTML/CSS layout, and visual design — is **© Ugur Ersoz. All rights reserved.**

Cloning, redeploying, repurposing, or republishing this site (in whole or in part) as your own personal portfolio is **not permitted**. Re-use of any content requires prior written permission.

---

## Contact

**Ugur Ersoz** — Berlin, Germany
[Website](https://ugrersoz.github.io/my-portfolio) · [LinkedIn](https://www.linkedin.com/in/ersozugur) · [GitHub](https://github.com/ugrersoz) · uersoz55@gmail.com
