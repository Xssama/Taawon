# taawon

## Lighthouse Performance Audit

Lighthouse audit results across all 5 pages of the Taawon project:

| Page | Performance | Accessibility | Best Practices | SEO |
| --- | --- | --- | --- | --- |
| **Home** (`index.html`) | 57 / 100 | 93 / 100 | 92 / 100 | 100 / 100 |
| **À Propos** (`a-propos.html`) | 38 / 100 | 91 / 100 | 96 / 100 | 91 / 100 |
| **Coopérative** (`cooperative.html`) | 62 / 100 | 100 / 100 | 92 / 100 | 100 / 100 |
| **Coopératives** (`cooperatives.html`) | 54 / 100 | 91 / 100 | 92 / 100 | 100 / 100 |
| **Partenaire** (`partenaire.html`) | 68 / 100 | 94 / 100 | 96 / 100 | 100 / 100 |
| **Average (Overall)** | **56 / 100** | **94 / 100** | **94 / 100** | **98 / 100** |

- **Audit device:** Mobile
- **Audit date:** October 18, 2026

### Tailwind CSS CDN trade-off

The current implementation loads Tailwind CSS through its CDN (`@tailwindcss/browser@4` on most pages, and `cdn.tailwindcss.com` on `a-propos.html`). This approach was chosen deliberately to keep the project simple to deploy as a static website on GitHub Pages, without requiring a Tailwind CSS build step in the deployment workflow. This was an intentional implementation trade-off made for deployment simplicity, rather than an accidental configuration error.

Technically, GitHub Pages does not require Tailwind CSS to be loaded through a CDN; a pre-compiled CSS bundle can also be built and deployed directly to GitHub Pages. Loading Tailwind via CDN is our current implementation choice.

In terms of performance, the CDN approach partly affects the scores across all pages because the browser must fetch the compiler runtime and parse the DOM dynamically to generate utility styles, which adds client-side JavaScript execution overhead. However, based on the audit findings, the CDN is not the sole factor impacting performance; asset delivery and high-resolution images also contribute significantly to metrics such as Largest Contentful Paint (LCP), especially on image-heavy pages like `a-propos.html` and `cooperatives.html`.
