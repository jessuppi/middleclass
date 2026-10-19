# Troubleshooting

This guide covers common integration issues when using the local `middleclass.css` file. Start by checking the HTML structure and the order of linked stylesheets before changing framework selectors.

## Styles Are Missing

- Confirm the stylesheet URL resolves from the **deployed page**, not only in a local preview. An example `/assets/middleclass.css` path is appropriate only if the website actually serves that file there.
- Verify that the page includes a `<link rel="stylesheet">` element and that the file was copied to the deployed output.
- Remember that sites hosted under a subdirectory may need a different path from sites hosted at a domain root.
- Load any project-specific stylesheet **after** MiddleClass so local overrides can take effect.

See the [README](../readme.md) for basic installation and [Customization](customization.md) for override patterns.

## Custom Styles Do Not Take Effect

- Check the browser's computed styles, source order, and selector specificity before adding `!important`.
- Public CSS custom properties use the `--mc-` prefix. Change them at an appropriate scope; consult [CSS variables](variables.md).
- Theme colors may come from automatic `prefers-color-scheme` styling or explicit `data-theme="light"` / `data-theme="dark"` attributes. Inspect which applies before overriding just one color.
- Prefer a separate site stylesheet to modifying the upstream framework file.

## Spacing or Width Looks Wrong

- `.container` supplies centered responsive page width and gutters; `.reading-width` limits text width and does not automatically center content. They can be combined.
- `.stack` owns spacing between its direct children by suppressing their external block margins. Nested content retains its own rhythm. Avoid adding extra child margins without checking the combined result.
- Headings from `h2` through `h6` intentionally have top margins; `h1` does not. The visual rhythm is a policy, not an accidental browser default.
- Cards, notices, fieldsets, and disclosures normalize child margins at their padded edges. Avoid compensating with arbitrary extra padding.
- For wide tables, use `.table-wrap`; for long links or code, inspect the containing layout for overflow.

Read [Spacing](spacing.md), [Sizing and units](sizing.md), and [Classes](classes.md) before introducing a global spacing override.

## Footer Does Not Stay at the Bottom

The built-in full-height page behavior assumes the common `header`–`main`–`footer` structure as direct body children. Additional wrappers, custom body rules, or a different application shell can alter it. Either use the conventional markup or override the document layout deliberately in the site's own stylesheet.

## Dropdown or Select Looks Wrong

- A supported dropdown is native `<details class="dropdown">` containing a direct `<summary>` followed by a direct `<ul>` of links. Different nesting can prevent the expected appearance.
- `.dropdown-start` and `.dropup` are optional direction modifiers; neither automatically detects room in the viewport.
- Check for clipping by ancestor `overflow` rules when an overlay panel is cut off.
- Single-select controls use a decorative chevron; multiple selects and listbox-style selects retain native appearance. Native controls can vary by browser, and forced-colors mode intentionally restores native single-select presentation.
- If a custom chevron is invisible, check `--mc-chevron-down` for native single-selects and `--mc-dropdown-chevron` for dropdowns, along with the relevant theme colors. Selects render the image directly as a background, while dropdowns use it as a mask.

See [Classes](classes.md), [Customization](customization.md), and [Browser Support](browser-support.md).

## Accessibility or Browser Differences

Use semantic elements and explicit form labels; CSS cannot repair missing HTML meaning. Test keyboard focus, text resizing, zoom, and narrow screens following [Accessibility](accessibility.md) and [Testing](testing.md). MiddleClass targets current stable modern browsers, not Internet Explorer or compatibility modes. An older browser may ignore a modern visual enhancement while retaining usable content.

## Is This a Framework Problem?

Reproduce the issue with plain semantic HTML and the unmodified `middleclass.css`. Temporarily remove site-specific overrides, wrappers, and scripts, then compare against the [demo](https://jessuppi.github.io/middleclass/). If the issue occurs only in site-specific code, fix it in that site's markup or stylesheet rather than adding a one-off rule to the framework. The demo's metadata, SEO setup, and hosting configuration do not apply to sites using MiddleClass.
