# Changelog

## 0.2.0

- introduced a built-in dropdown chevron using Font Awesome Free's `chevron-down` icon so sites that already use icons get a polished, consistent control without adding icon markup or recreating the shape in each project
- embedded the icon as an SVG data URI rendered through a `currentColor` CSS mask, keeping its color, sizing, alignment, and open or dropup rotation under MiddleClass control
- added `--mc-chevron-font-awesome` for the bundled default and inheritable `--mc-dropdown-chevron` overrides so sites can replace the icon globally, within a section, or on an individual dropdown
- added Font Awesome source, modification, and CC BY 4.0 attribution for the bundled third-party icon

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
