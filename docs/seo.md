# SEO

MiddleClass is a CSS framework, not an SEO toolkit. This document separates what the reusable framework provides from the metadata and indexing choices made for this repository's own demo website.

## Framework Scope

The reusable product is `middleclass.css`. It styles ordinary semantic HTML, including headings, links, navigation, and content, with responsive defaults and a small optional class API. It requires no JavaScript or build step. These characteristics can help authors build readable, crawlable pages, but CSS alone cannot provide search metadata or guarantee indexing, rankings, or rich results.

MiddleClass does **not** generate, inject, or manage:

- HTML titles, meta descriptions, canonical URLs, or robots directives
- Open Graph or social card metadata and images
- JSON-LD or other structured data
- XML sitemaps or `robots.txt`
- redirects, HTTP headers, site routing, analytics, or search-engine verification

These are **site-level responsibilities**, not core CSS features. Do not add SEO-specific classes, metadata generators, or site configuration to `middleclass.css` to solve a demo-site SEO need.

## Guidance for Sites Using MiddleClass

Each site author should supply suitable HTML, URLs, and server or hosting configuration for their own project. Depending on the site, that may include:

- A unique, descriptive `<title>` and useful meta description for important pages
- Canonical URLs where appropriate, using the site's actual public domain and URL paths
- Descriptive headings, meaningful links, accessible images, and crawlable navigation
- Open Graph and social preview metadata when links are shared
- Accurate structured data only for content and entities actually represented on the page
- A sitemap for larger sites when useful, plus host-level crawling rules if needed

Do not copy this repository's canonical URL, demo description, or MiddleClass-specific JSON-LD into a different website. The demo's SEO implementation is an example of site-authored markup, not an API or bundled feature of the framework.

## This Repository's Demo Website

The public demo is `https://jessuppi.github.io/middleclass/`. Its HTML lives in the repository's `index.html`, **separate from the core stylesheet**.

Currently maintained in `index.html`:

- A descriptive page title and meta description
- A canonical URL for the public GitHub Pages demo
- Open Graph website, site name, title, description, and URL metadata
- A basic `twitter:card` value of `summary`
- A favicon
- JSON-LD using `SoftwareSourceCode` for MiddleClass and `WebSite` for the demo, with distinct linked identifiers

The demo's JSON-LD describes this project; it is not automatically applied to sites using the stylesheet. Structured data does not guarantee a search-result enhancement. Keep the description, URLs, and software version in the demo metadata accurate when the project changes.

### Social Preview Image

A dedicated preview PNG has not yet been added. Accordingly, the demo currently omits `og:image` and uses `twitter:card=summary`, not `summary_large_image`. Add image references only when the image exists at its published URL; then update the card type if appropriate. This is a **demo-site task**, not a MiddleClass core feature.

## Sitemaps and Robots on GitHub Pages

GitHub Pages can serve an XML sitemap from a project site, for example at `https://jessuppi.github.io/middleclass/sitemap.xml`. A sitemap is optional for this single-page demo, so the repository does not currently maintain one. It may be added if the demo grows to include multiple indexable pages.

The `robots.txt` standard is **host-root scoped**: for this demo it would be read from `https://jessuppi.github.io/robots.txt`, not `https://jessuppi.github.io/middleclass/robots.txt`. Adding `robots.txt` inside this project repository's `/middleclass/` path would not establish crawling rules for the host. Host-root rules are outside the scope of this project-site repository, so no `robots.txt` is maintained here.

These are choices specific to the current GitHub Pages URL structure; sites with their own domains or hosting arrangements must make their own decisions. Neither a sitemap nor `robots.txt` is required by MiddleClass, and neither is part of the distributed CSS.

## Maintenance Boundary

When changing SEO for the demo, edit the demo HTML or its site-specific assets, not the core CSS or public class API. When modifying core styles, keep semantic markup and accessible presentation in mind, but do not treat the framework as responsible for each adopting site's SEO setup.

See [Releases](releases.md) for keeping demo version metadata aligned with CSS releases and [Localization](localization.md) for language-specific responsibilities that belong to site authors.
