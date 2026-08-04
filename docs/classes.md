# Classes

MiddleClass is classless-first, but it provides a small public class API for layout and presentation choices that semantic HTML cannot express by itself.

This file is the canonical reference for every supported public class. Class names not listed here should be treated as site-specific rather than part of MiddleClass's public API.

## Public Class Overview

MiddleClass intentionally keeps its public class API small:

- Layout: `.container`, `.reading-width`, `.stack`, `.cluster`, `.columns`, and `.push-end`
- Typography: `.brand` and `.eyebrow`
- Buttons and variants: `.button`, `.secondary`, and `.outline`
- Content components: `.card`, `.notice`, `.success`, `.warning`, `.danger`, `.dropdown`, `.dropdown-start`, and `.dropup`
- Supporting behavior: `.table-wrap`, `.muted`, and `.screen-reader-text`

Semantic element defaults remain the foundation of the framework, and site-specific presentation should remain in the site's own stylesheet.

## Layout

Layout classes control internal arrangement and remain externally marginless by default. The parent containing a layout class should provide any vertical spacing before or after it.

### `.container`

Centers content within the site width and responsive page gutters.

```html
<div class="container">
	...
</div>
```

The maximum width is controlled by `--mc-content-width`, and the side gutters are controlled by `--mc-gutter`.

### `.reading-width`

Limits long-form content to a comfortable reading width without centering it automatically.

```html
<article class="reading-width">
	...
</article>
```

The width is controlled by `--mc-reading-width`.

### `.stack`

Arranges direct children vertically with consistent spacing.

```html
<div class="stack">
	<section>...</section>
	<section>...</section>
</div>
```

MiddleClass removes the direct children's outer block margins so the stack gap is the single source of spacing between them. Content inside each child keeps its normal document rhythm.

Override the spacing for one stack with `--mc-stack-space`:

```html
<div class="stack" style="--mc-stack-space: 2rem;">
	...
</div>
```

### `.cluster`

Arranges related items in a wrapping horizontal row with centered cross-axis alignment.

```html
<div class="cluster">
	<a class="button" href="/download/">Download</a>
	<a class="button outline" href="/docs/">Documentation</a>
</div>
```

`.cluster` controls only the arrangement of its children and intentionally adds no outer margin. When a cluster should participate in normal document rhythm, apply the class to an appropriate semantic element:

```html
<p class="cluster">
	<a class="button" href="/download/">Download</a>
	<a class="button outline" href="/docs/">Documentation</a>
</p>
```

Here the paragraph keeps its normal bottom margin while `.cluster` controls the links' internal arrangement. Use a structural wrapper such as `<div>` when the group should remain marginless, or place larger groups inside a parent layout such as `.stack`.

Override the spacing for one cluster with `--mc-cluster-space`.

On narrow screens, direct button-like children can grow to share available row width.

### `.columns`

Creates responsive equal-width columns that collapse naturally when space becomes limited.

```html
<div class="columns">
	<article class="card">...</article>
	<article class="card">...</article>
</div>
```

Override the spacing for one column group with `--mc-columns-space`.

### `.push-end`

Moves one item to the inline end of a horizontal flex layout when free space is available.

```html
<nav aria-label="Primary navigation">
	<ul>
		<li><a href="/">Home</a></li>
		<li class="push-end"><a href="/account/">Account</a></li>
	</ul>
</nav>
```

The inline end is the right side in left-to-right documents and the left side in right-to-left documents. The class has no useful pushing effect unless the parent is a horizontal flex container.

## Typography

### `.brand`

Styles a site or product name as prominent navigation text without making it a document heading.

```html
<nav aria-label="Primary navigation">
	<ul>
		<li><a class="brand" href="/">Example</a></li>
		<li><a href="/about/">About</a></li>
	</ul>
</nav>
```

Use a link when selecting the brand should return to the home page. The class may also be applied to an appropriate text element when the brand is not a link. It changes typography only and does not create navigation or heading semantics.

### `.eyebrow`

Styles compact contextual text above a heading with a muted color, small uppercase lettering, bold weight, letter spacing, and generous separation from the heading.

```html
<p class="eyebrow">Lightweight CSS framework</p>
<h1>Pragmatic CSS for clean static websites</h1>
```

Use concise wording that communicates a category, product type, or section context rather than decorative filler. The class changes presentation only, so use an element that remains appropriate for the content, usually a paragraph.

## Buttons and Variants

### `.button`

Gives a link the same button presentation as native buttons and button-type inputs.

```html
<a class="button" href="/download/">Download</a>
```

Use native `<button>` elements for actions and `.button` links for navigation. Direct SVG children receive consistent spacing and are normalized to `1em`; MiddleClass does not provide a general-purpose icon library.

### `.secondary`

Applies the secondary button color treatment.

```html
<button class="secondary" type="button">Cancel</button>
<a class="button secondary" href="/other/">Other option</a>
```

Supported on native buttons, `.button` links, and button-type inputs.

### `.outline`

Uses a transparent button background with an accent border and text.

```html
<a class="button outline" href="/learn/">Learn more</a>
```

It may be combined with `.secondary`:

```html
<a class="button secondary outline" href="/source/">View source</a>
```

The combined treatment uses neutral text and border colors with a subtle neutral hover surface. Both variants are supported on native buttons, `.button` links, and button-type inputs.

## Content Components

### `.card`

Creates a contained surface with padding, a border, and rounded corners.

```html
<article class="card">
	<h2>Card title</h2>
	<p>Card content.</p>
</article>
```

The first and last children have their outer vertical margins normalized so the card spacing remains predictable.

### `.notice`

Creates a highlighted message with a leading accent border.

```html
<aside class="notice">
	<p><strong>Note:</strong> This is useful contextual information.</p>
</aside>
```

Combine it with `.success`, `.warning`, or `.danger` when the status is meaningful.

### `.success`

Changes the accent of a `.notice` to the success color.

```html
<div class="notice success">Saved successfully.</div>
```

This class changes presentation only. The content must still communicate the successful state in words.

### `.warning`

Changes the accent of a `.notice` to the warning color.

```html
<div class="notice warning">Review these settings before continuing.</div>
```

This class changes presentation only. Do not rely on color alone.

### `.danger`

Changes the accent of a `.notice` to the danger color.

```html
<div class="notice danger">The operation could not be completed.</div>
```

This class changes presentation only. Do not rely on color alone.

### `.dropdown`

Turns a native `<details>` element into an overlaid link menu. Unclassed `<details>` elements remain block-style disclosures for expandable content.

```html
<details class="dropdown">
	<summary>Products</summary>
	<ul>
		<li><a href="/products/one/">Product One</a></li>
		<li><a href="/products/two/">Product Two</a></li>
	</ul>
</details>
```

The supported structure is a direct `<summary>` followed by a direct `<ul>`. By default, the panel opens below the trigger and its inline-end edge aligns with the trigger's inline-end edge. The open list overlays nearby content instead of shifting the layout, while opening and closing remain native `<details>` behavior.

The trigger uses a bundled Font Awesome chevron by default. A site can replace it globally or within a particular subtree by overriding `--mc-dropdown-chevron` with another mask-compatible image:

```css
:root {
	--mc-dropdown-chevron: url("data:image/svg+xml,...");
}
```

MiddleClass owns the chevron's size, color, alignment, direction, and rotation. See [CSS variables](variables.md) for the complete override guidance.

The links remain ordinary links. Do not add application-style `menu` or `menuitem` roles. When open, a pointer click outside the panel closes the disclosure through an invisible viewport layer owned by the native `<summary>`; no JavaScript is required.

The outside-click dismissal pattern is adapted from the MIT-licensed [Pico CSS](https://github.com/picocss/pico) dropdown implementation.

### `.dropdown-start`

Changes a `.dropdown` panel from inline-end alignment to inline-start alignment. On a left-to-right page, this aligns the panel's left edge with the trigger's left edge. On a right-to-left page, it aligns their right edges.

```html
<details class="dropdown dropdown-start">
	<summary>Products</summary>
	<ul>
		<li><a href="/products/one/">Product One</a></li>
		<li><a href="/products/two/">Product Two</a></li>
	</ul>
</details>
```

Use this modifier when the trigger is near the inline-start side of its container. It has no supported standalone behavior without `.dropdown`.

### `.dropup`

Makes a `.dropdown` panel open above its trigger instead of below it. The chevron also points upward while closed and downward while open.

```html
<details class="dropdown dropup">
	<summary>Products</summary>
	<ul>
		<li><a href="/products/one/">Product One</a></li>
		<li><a href="/products/two/">Product Two</a></li>
	</ul>
</details>
```

Use this modifier where space below the trigger is limited. It does not detect viewport space automatically and has no supported standalone behavior without `.dropdown`.

The alignment and direction modifiers may be combined:

```html
<details class="dropdown dropdown-start dropup">
	<summary>Products</summary>
	<ul>
		<li><a href="/products/one/">Product One</a></li>
		<li><a href="/products/two/">Product Two</a></li>
	</ul>
</details>
```

## Supporting Behavior

### `.table-wrap`

Allows a wide table to scroll horizontally without forcing the entire page to overflow.

```html
<div class="table-wrap">
	<table>
		...
	</table>
</div>
```

Use the class on a wrapper around the table, not on the table itself.

### `.muted`

Applies the secondary text color.

```html
<p class="muted">Supporting information</p>
```

Muted text should remain readable and should not be used for information that needs strong emphasis.

### `.screen-reader-text`

Visually hides text while keeping it available to assistive technology.

```html
<a href="/search/">
	<svg aria-hidden="true" focusable="false" viewBox="0 0 24 24">...</svg>
	<span class="screen-reader-text">Open search</span>
</a>
```

Use this class for concise accessible labels or supporting text that genuinely should not be visible. Prefer clear visible wording when it can solve the problem directly.

## Combining Classes

Classes may be combined when their roles are compatible:

```html
<a class="button secondary outline" href="/source/">View source</a>
<div class="notice warning">Check this setting.</div>
<details class="dropdown dropdown-start dropup">...</details>
```

Avoid adding framework classes merely to reproduce individual CSS declarations. Site-specific layouts and visual treatments should remain in the site's own stylesheet.

## Related Documentation

- [Architecture](architecture.md) explains why these classes are part of the public API.
- [Accessibility](accessibility.md) covers author responsibilities and component-specific accessibility guidance.
- [CSS variables](variables.md) documents the values used to customize shared styling.
- [Sizing and units](sizing.md) explains MiddleClass's unit choices.
