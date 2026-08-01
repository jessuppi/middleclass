# Changelog

## 0.2.0

- replaced the CSS border-built dropdown chevron with the Font Awesome Free `chevron-down` path embedded as an SVG data URI and rendered through a `currentColor` CSS mask
- added `--mc-chevron-font-awesome` for the bundled source image and inheritable `--mc-dropdown-chevron` overrides for global, scoped, or custom mask replacement
- normalized the masked chevron to `0.8em`, retained automatic open and dropup rotation, and added Font Awesome source, modification, and CC BY 4.0 attribution

## 0.1.1

- added outside-click closing for dropdown menus without JavaScript
- removed default top margins from `h2` through `h6` so preceding flow elements own vertical spacing
- normalized padded semantic component edges, including content after legends and disclosure summaries, and trailing figure caption spacing
- normalized trailing nested list spacing so parent-level items keep the standard gap

## 0.1.0

- added the initial classless-first stylesheet for semantic static websites
- added light, dark, and system-aware color themes with explicit theme overrides
- added the public `--mc-*` custom-property namespace for colors, typography, spacing, sizing, and layout
- added responsive containers, reading widths, stacks, clusters, columns, and logical alignment
- added buttons and variants, cards, notices, responsive tables, disclosures, and dropdown menus
- added accessible focus styles, form controls, disabled states, touch-friendly sizing, and visually hidden text
- added narrow-screen behavior, long-content safeguards, and predictable document and component spacing
- added the live demonstration page, MIT license, and project documentation
