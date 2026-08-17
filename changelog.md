# Changelog

## 0.4.2

- changed `.reading-width` to a max-width constraint so it can be combined with `.container` without overriding responsive page gutters

## 0.4.1

- gave `.notice` the standard `--mc-space-5` (`1.5rem`) bottom margin used by paragraphs and other ordinary block content

## 0.4.0

- set default top margins to `3rem` for `h2` and `2rem` for `h3` through `h6` so section and subsection headings have clearer separation from preceding content
- retained the `0` default top margin on `h1`
- retained the existing `1rem` bottom margin for all heading levels
- kept `.stack` gap behavior unchanged by continuing to normalize direct-child block margins

## 0.3.2

- fixed `.stack` direct-child margin normalization so later typography rules such as `.eyebrow` no longer override stack `gap` spacing

## 0.3.1

- made the document body a full-height column flex container and set `main` to `flex: 1`, so standard `header`-`main`-`footer` pages keep the footer at the bottom of short viewports without project-specific CSS

## 0.3.0

- added the public `.brand` typography class for prominent site or product names in navigation
- added the public `.eyebrow` typography class for compact contextual text above headings

## 0.2.0

- introduced a built-in dropdown chevron using Font Awesome Free's `chevron-down` icon so sites that use icons can ship a polished, consistent control without adding icon markup or recreating the shape in each project
- retained the original icon path in a percent-encoded SVG data URI with a cropped `viewBox`, then applied it as a CSS mask over `currentColor` for consistent sizing, alignment, theming, open-state rotation, and dropup orientation
- added `--mc-chevron-down-font-awesome` for the bundled asset, `--mc-chevron-down` for the shared framework default, and inheritable `--mc-dropdown-chevron` overrides for dropdown-specific customization
- added the Font Awesome source, modification details, and complete upstream license notices in root-level `notices.md`

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
