# Ugur Ersoz — Portfolio

Personal portfolio of Ugur Ersoz, a product developer and researcher in life sciences and digital health, based in Berlin.

[Live website](https://ugrersoz.github.io/)

## Design and content

A restrained, project-first portfolio with neutral colors, system typography, subtle dividers, and concise editorial copy. The site introduces Ugur’s focus, then presents selected work, experience, education, skills, writing, and contact details. Numbering is omitted; a reversible portrait adds a personal interaction without interrupting the reading flow.

- Six projects with short summaries and expandable descriptions, images, and original project links.
- Experience and education presented as native HTML disclosures, usable without JavaScript.
- Responsive layouts for desktop and mobile, visible keyboard focus, and a skip-to-content link.
- Image previews use a native modal dialog with Escape dismissal, descriptive text, and focus restoration.
- Reduced-motion preferences are respected. Off-screen portfolio images load lazily.
- Existing canonical links, social preview assets, and structured data are retained.

The interface and professional content are in English.

## Structure

```text
index.html             Page content, styles, and small interaction script
images/                Portfolio images, certificates, and icons
versions/              Previous design snapshots
.github/workflows/     Existing GitHub Pages deployment
site.webmanifest       App metadata
robots.txt             Crawler directives
sitemap.xml            Sitemap
```

The site uses HTML, CSS, and vanilla JavaScript. It has no package dependencies or build step. Open `index.html` directly, or serve the repository with any static HTTP server.

## Deployment

The repository is `ugrersoz/ugrersoz.github.io`. GitHub Actions prepares the public files and publishes them to `gh-pages` when changes are pushed to `main`. GitHub Pages must serve the root of `gh-pages`. The workflow stamps the footer and sitemap using the latest commit date in Europe/Istanbul. Local edits do not change the live website until published. The old `/my-portfolio/` address redirects to the root site.

## Search discovery

The canonical URL, structured person data, social-preview URLs, app manifest, and sitemap use `https://ugrersoz.github.io/`. The public `robots.txt` allows crawling and points to the sitemap. Previous snapshots and maintenance files are excluded from the published artifact.

For Google Search Console, add the URL-prefix property `https://ugrersoz.github.io/`, verify ownership using an HTML tag in `index.html` (or a verification file explicitly included in the publishing step), submit `https://ugrersoz.github.io/sitemap.xml`, and request indexing for the homepage. Verification requires the owner's Google account. Crawling and indexing are controlled by Google and are not guaranteed by the site configuration.

## Validation

For the September 2026 redesign, source checks covered HTML nesting, duplicate IDs, section targets, local asset paths, JavaScript syntax, and preservation of existing project links and images. A focused script also checked modal opening, image descriptions, scroll restoration, and focus return. The local preview returned HTTP 200. These checks do not constitute browser-based visual or accessibility testing.

## License & usage

This repository is public for transparency and reference. Deployment workflows and configuration files are released under the [MIT License](LICENSE). All site content, photographs, certificates, HTML/CSS layout, and visual design are © Ugur Ersoz. All rights reserved. See [LICENSE](LICENSE) for the full dual-scope terms.

## Contact

[LinkedIn](https://www.linkedin.com/in/ersozugur) · [GitHub](https://github.com/ugrersoz) · [Email](mailto:uersoz55@gmail.com)
