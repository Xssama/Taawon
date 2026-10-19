# taawon

## Lighthouse Performance Audit

Lighthouse audit results for the current state of the Taawon project:

| Category | Score |
| --- | --- |
| Performance | 68 / 100 |
| Accessibility | 93 / 100 |
| Best Practices | 92 / 100 |
| SEO | 100 / 100 |

- **Audit device:** Mobile
- **Audit date:** October 18, 2026

*(For reference, the desktop audit yielded: Performance: 70, Accessibility: 93, Best Practices: 96, SEO: 100).*

### Tailwind CSS CDN trade-off

The current implementation loads Tailwind CSS through its CDN (`@tailwindcss/browser@4`). This approach was chosen deliberately to keep the project simple to deploy as a static website on GitHub Pages, without requiring a Tailwind CSS build step in the deployment workflow. This was an intentional implementation trade-off made for deployment simplicity, rather than an accidental configuration error.

Technically, GitHub Pages does not require Tailwind CSS to be loaded through a CDN; a pre-compiled CSS bundle can also be built and deployed directly to GitHub Pages. Loading Tailwind via CDN is our current implementation choice.

In terms of performance, the CDN approach partly affects the score because the browser must fetch the compiler runtime and parse the DOM dynamically to generate utility styles, which adds client-side JavaScript execution overhead (~290 ms CPU time on mobile). However, based on the audit findings, the CDN is not the sole factor impacting performance; asset delivery and high-resolution images also contribute to metrics such as Largest Contentful Paint (LCP).
