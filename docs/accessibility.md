# Accessibility

StyleWire aims to provide accessible CSS defaults for semantic static websites. It does not guarantee that every site using the framework is accessible, because markup, content, scripting, and local overrides remain the site's responsibility.

StyleWire is still pre-1.0, so this guidance describes the current direction rather than a permanent compatibility contract.

## Framework Baseline

StyleWire currently provides:

- visible keyboard focus through `:focus-visible`
- light and dark defaults that aim to meet common WCAG AA contrast thresholds where StyleWire controls both colors
- native form controls and button behavior rather than custom replacements
- minimum heights for text fields and button-like controls intended to support practical touch targets
- layouts that can wrap and adapt on narrow screens
- a `.screen-reader-text` class for visually hidden accessible text
- no bundled JavaScript, animation, or interactive widget behavior

Framework changes should preserve native semantics, keyboard access, text resizing, browser font preferences, and assistive-technology access.

## Author Responsibilities

Sites using StyleWire should still provide:

- meaningful landmarks and heading order
- labels for form controls
- useful alternative text for informative images
- clear link and button text
- keyboard support for any site-specific interactive behavior
- status or error text that does not rely on color alone
- accessible contrast after overriding framework colors

Classes such as `.success`, `.warning`, and `.danger` change presentation only. The surrounding content must communicate the actual meaning.

## Details and Dropdowns

Unclassed `details` elements remain block-style disclosures for expandable content. StyleWire also supports `details.dropdown` when the same native disclosure behavior should present a direct `ul` as an overlaid link menu without shifting nearby layout.

The `summary` remains the native keyboard-operable trigger, and links inside the list remain ordinary links. Authors should use clear summary text, keep each destination understandable out of context, and preserve the required direct structure:

```html
<details class="dropdown">
	<summary>Products</summary>
	<ul>
		<li><a href="/products/one/">Product One</a></li>
		<li><a href="/products/two/">Product Two</a></li>
	</ul>
</details>
```

The CSS-only component does not add application-style menu roles or JavaScript behavior such as closing when a user clicks elsewhere. Ordinary navigation links should not be given `menu` or `menuitem` roles.

## Visually Hidden Text

Use `.screen-reader-text` when text should remain available to assistive technology without being visually displayed. Decorative icon markup should be hidden from assistive technology:

```html
<a href="/search/">
	<svg aria-hidden="true" focusable="false" viewBox="0 0 24 24">
		<path d="M11 4a7 7 0 1 0 4.9 12l4 4 1.4-1.4-4-4A7 7 0 0 0 11 4Zm0 2a5 5 0 1 1 0 10 5 5 0 0 1 0-10Z"></path>
	</svg>
	<span class="screen-reader-text">Open search</span>
</a>
```

Do not use visually hidden text to repair unclear structure when visible wording or better semantic markup would solve the problem more directly.

## Motion

StyleWire currently includes no animations or transitions. If motion is added later, it should remain limited and respect `prefers-reduced-motion` where appropriate.

## Basic Testing

Before releasing a framework change or a site built with StyleWire, check at least:

1. Keyboard navigation and visible focus.
2. Light and dark color schemes.
3. Browser zoom at 200%.
4. A narrow viewport around 320px wide.
5. Form labels, disabled states, and validation messaging.
6. A brief screen-reader check for important page structure and controls.

Automated tools can help identify problems, but they do not replace manual keyboard, zoom, and assistive-technology testing.

## Scope

StyleWire does not currently claim formal WCAG conformance. The project should continue improving its defaults while keeping the framework small, semantic, and easy for sites to override.
