# Testing

MiddleClass is a small CSS framework without a build step or JavaScript test runner. Testing primarily means reviewing source changes and manually exercising the [demo page](https://jessuppi.github.io/middleclass/) in browsers. The demo includes a dedicated **Layout and rhythm tests** section with intentionally repetitive content to reveal layout regressions; it is a test fixture, not a feature requirement for sites using the framework.

## What to Test

For any change to `middleclass.css`, first review the affected selectors, variables, and public classes against [Architecture](architecture.md), [Classes](classes.md), and [Spacing](spacing.md). Then check the changed behavior in the demo.

### Document and Layout

- Standard `header`–`main`–`footer` flow, including the footer on short pages
- `.container`, `.reading-width`, `.stack`, `.cluster`, `.columns`, and `.push-end`
- Vertical rhythm between paragraphs, headings, lists, tables, and figures
- Padded edges for cards, notices, blockquotes, fieldsets, and disclosures
- Long URLs, code samples, narrow tables, and nested content without page-wide overflow

### Interactive and Accessible States

- Buttons and links in default, hover, focus, active, and disabled states as applicable
- Native form controls, labels, single-selects, and multiple-selects
- `details` disclosures and `.dropdown`, `.dropdown-start`, and `.dropup` combinations
- Keyboard tab order, visible `:focus-visible`, and closing native dropdowns
- Light/dark themes, custom theme overrides, and forced-colors behavior where supported

### Viewports and Browsers

- A narrow viewport around 320px, common phone widths, and desktop widths
- Browser zoom at 200% and increased default text size
- Current stable Chrome, Edge, Firefox, and Safari as practical
- Right-to-left layout when the change affects logical directions

See [Browser Support](browser-support.md) for the target policy and [Accessibility](accessibility.md) for additional checks. Do not claim a browser was tested if it was not.

## Regression Review Workflow

1. Read the relevant docs and identify which public behavior or variable may change.
2. Edit the smallest necessary section of `middleclass.css`; avoid unrelated formatting changes.
3. Inspect the demo's feature tour and **Layout and rhythm tests** area at several sizes.
4. Test impacted keyboard, form, theme, and browser cases.
5. Review the change for unintended effects on semantic elements and existing classes.
6. When framework behavior changes, update the relevant documentation and [Changelog](../changelog.md) as appropriate, following the [Releases](releases.md) guide.

This is a **manual checklist**, not a claim that an automated suite exists or that any specific check has already passed. When real-device or cross-browser checks cannot be performed, record the limitation instead of marking them complete.

## Core vs. Demo

Changes to the demo's copy, metadata, images, documentation links, or SEO do **not** require modifying the distributed CSS or bumping its version. Demo-specific presentation used to showcase the framework should not become a new public class unless it meets the [class admission rules](architecture.md).
