# Browser Support

MiddleClass targets the current stable versions of Chrome, Edge, Firefox, and Safari, including their mobile counterparts where applicable. This is the existing modern-browser policy from [Architecture](architecture.md), not a promise that every release has been tested on every device and operating system.

## Supported Baseline

- **Target:** Current stable Chrome, Edge, Firefox, and Safari.
- **Not targeted:** Internet Explorer, outdated browser releases, and special compatibility modes.
- **No compatibility toolchain:** The distributed `middleclass.css` is authored CSS; there are no transpilers, polyfill bundles, or JavaScript requirements.
- **No fixed minimum-version matrix:** The project has not established or certified specific minimum browser versions. Do not infer a tested version cutoff from this page.

Basic typography and document structure should remain understandable when an optional visual enhancement is unsupported. Core navigation, form access, readable content, and focus visibility should not depend on a browser-specific trick.

## Native and Modern CSS

MiddleClass relies on browser-native HTML behavior for buttons, form controls, and `details` / `summary` disclosures. Dropdown menus use `details.dropdown` and CSS instead of JavaScript. Site authors should test these interactions with pointer and keyboard input rather than assuming a CSS-only component behaves identically across engines.

The stylesheet also uses modern CSS, including custom properties, Grid, flexbox, logical properties, `:focus-visible`, `:has()`, and `color-scheme`. Some visual details may differ between supported browser engines, and some selectors or enhancements may be ignored by older browsers. For example, the `:has()` selector helps normalize figure spacing; it is not required for the figure's underlying semantic content.

Select controls normally use the shared decorative chevron while retaining native selection behavior. Multiple selects and listbox-style selects keep their native treatment, and forced-colors mode includes a fallback for single-select appearance.

## Browser and Accessibility Checks

Before releasing significant styling changes, check current stable Chrome, Edge, Firefox, and Safari as practical, and use the [Testing](testing.md) checklist for manual regression coverage. Include:

- Narrow mobile and wider desktop viewports, plus zoom and text resizing
- Keyboard focus, disclosure behavior, form controls, and horizontal overflow
- Light, dark, and forced-colors modes where available
- Right-to-left layout when changing logical alignment or dropdown behavior

A visual mismatch should be assessed for actual usability impact rather than automatically introducing browser-specific CSS. If an issue cannot be verified on a browser, describe it as unverified rather than claiming compatibility.

## Responsibilities and Scope

MiddleClass maintains the shared CSS baseline. The adopting website controls its HTML, external scripts, custom overrides, hosting, and any browser support requirements stricter than this baseline. See [Customization](customization.md), [Accessibility](accessibility.md), and [Scope](scope.md).

The GitHub Pages [demo](https://jessuppi.github.io/middleclass/) is a useful manual test fixture, **not a published browser-compatibility certification**.
