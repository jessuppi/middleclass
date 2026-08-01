# Customization

MiddleClass is designed to provide useful defaults without preventing a site from establishing its own visual identity. Most customization should happen in a site stylesheet loaded after `middleclass.css`.

This guide covers the common customization workflow. See [CSS variables](variables.md) for the complete variable reference.

## Recommended Setup

Load MiddleClass first and the site's stylesheet second:

```html
<link rel="stylesheet" href="/assets/middleclass.css">
<link rel="stylesheet" href="/assets/site.css">
```

The later stylesheet can override documented variables, semantic element styles, and public classes without modifying the framework file.

Keeping site changes separate makes MiddleClass easier to update and keeps project-specific decisions out of the framework source.

## Global Variables

All public MiddleClass variables use the `--mc-` prefix. Override shared values on `:root`:

```css
:root {
	--mc-content-width: 80rem;
	--mc-reading-width: 44rem;
	--mc-gutter: clamp(1rem, 5vw, 3rem);
	--mc-radius: 0.25rem;
}
```

Use variables for shared framework choices such as typography, widths, spacing, colors, borders, and radii. Use ordinary site CSS for isolated presentation that does not need to affect the framework globally.

There is normally no reason to edit `middleclass.css` directly.

## Typography

MiddleClass uses system font stacks by default and does not bundle fonts. A site may load its own fonts and override the typography variables:

```css
:root {
	--mc-font-sans: "Example Sans", system-ui, sans-serif;
	--mc-font-mono: "Example Mono", ui-monospace, monospace;
	--mc-font-size: 1.0625rem;
	--mc-line-height: 1.65;
}
```

Preserve a suitable fallback stack in case a custom font does not load. After changing font family, size, or line height, review headings, form controls, buttons, navigation, code, and long-form content.

## Widths, Gutters, and Shape

The main geometry variables can adapt MiddleClass to a compact blog, documentation site, business site, or wider marketing layout:

```css
:root {
	--mc-content-width: 76rem;
	--mc-reading-width: 42rem;
	--mc-gutter: clamp(1rem, 4vw, 2.5rem);
	--mc-radius: 0.375rem;
	--mc-radius-small: 0.25rem;
	--mc-border-width: 1px;
}
```

`--mc-content-width` controls `.container`, while `--mc-reading-width` controls `.reading-width`. The gutter remains responsive and should continue to leave comfortable space on narrow screens.

See [Sizing and units](sizing.md) for the framework's unit choices.

## Spacing

MiddleClass provides a shared spacing scale from `--mc-space-1` through `--mc-space-8`. A site may adjust the scale globally, but the values should remain ordered from smallest to largest:

```css
:root {
	--mc-space-1: 0.25rem;
	--mc-space-2: 0.5rem;
	--mc-space-3: 0.75rem;
	--mc-space-4: 1rem;
	--mc-space-5: 1.5rem;
	--mc-space-6: 2.25rem;
	--mc-space-7: 3.25rem;
	--mc-space-8: 4.5rem;
}
```

Large spacing changes affect document rhythm, forms, navigation, buttons, components, and responsive layouts. Review the whole site rather than one component in isolation.

See [Spacing](spacing.md) for spacing ownership and layout behavior.

## Individual Layout Instances

The layout classes expose local gap variables:

- `--mc-stack-space` for `.stack`
- `--mc-cluster-space` for `.cluster`
- `--mc-columns-space` for `.columns`

Set one directly on the relevant component:

```html
<div class="columns" style="--mc-columns-space: 2rem;">
	...
</div>
```

A reusable site class is preferable when the same adjustment appears repeatedly:

```css
.feature-columns {
	--mc-columns-space: 2rem;
}
```

```html
<div class="columns feature-columns">
	...
</div>
```

These variables inherit, so place them on the narrowest element that should control the matching layout.

## Colors and Themes

MiddleClass follows the operating system color preference when the root element has no `data-theme` attribute. A site can force a theme with:

```html
<html lang="en" data-theme="light">
```

or:

```html
<html lang="en" data-theme="dark">
```

Interactive theme-switching behavior belongs to the site. MiddleClass only provides the CSS theme states.

Color overrides should account for the default light theme, automatic dark mode, and any explicit themes the site supports.

### Light Theme

Override the default and explicit light-theme values together:

```css
:root,
[data-theme="light"] {
	--mc-accent: #6b3fc8;
	--mc-accent-hover: #5630a7;
	--mc-accent-text: #ffffff;
}
```

### Automatic Dark Theme

Match MiddleClass's automatic dark-theme selector:

```css
@media (prefers-color-scheme: dark) {
	:root:not([data-theme]) {
		--mc-accent: #b69cff;
		--mc-accent-hover: #d1c1ff;
		--mc-accent-text: #15101d;
	}
}
```

### Explicit Dark Theme

Override the forced dark theme separately:

```css
[data-theme="dark"] {
	--mc-accent: #b69cff;
	--mc-accent-hover: #d1c1ff;
	--mc-accent-text: #15101d;
}
```

Treat related colors as a group. Review accent, hover, accent text, backgrounds, surfaces, borders, muted text, focus outlines, and status colors together. The site is responsible for preserving readable contrast after changing the defaults.

## Scoped Customization

CSS variables inherit, so a section can establish a local treatment without affecting the rest of the page:

```css
.promotion {
	--mc-accent: #9b2c2c;
	--mc-accent-hover: #7f1d1d;
	--mc-radius: 1rem;
}
```

Links, buttons, and components inside `.promotion` use those values. Keep the selector as narrow as the intended effect because nested elements inherit the override.

Scoped color changes must still provide appropriate contrast against the section's backgrounds and surfaces.

## Semantic Elements and Public Classes

Variables are the preferred way to change shared visual choices, but a site may also override ordinary elements and MiddleClass classes in its own stylesheet:

```css
article h2 {
	letter-spacing: -0.015em;
}

.pricing-card {
	border-width: 2px;
}
```

```html
<article class="card pricing-card">
	...
</article>
```

Use site-specific classes for presentation that belongs to one project. Do not rely on undocumented internal selectors as stable API.

MiddleClass keeps selector specificity low so a later site stylesheet can normally override it without `!important`. See [Classes](classes.md) for the supported public class API.

## Dropdown Chevron

Dropdowns use a bundled Font Awesome chevron by default. Replace it globally with another mask-compatible image:

```css
:root {
	--mc-dropdown-chevron: url("data:image/svg+xml,...");
}
```

Or replace it only within one menu or section:

```css
.account-menu {
	--mc-dropdown-chevron: url("data:image/svg+xml,...");
}
```

MiddleClass continues to control the chevron's size, color, alignment, direction, and open-state rotation. The replacement should therefore be a simple single-color shape suitable for use as a CSS mask.

## What Belongs in Site CSS

Use the site's own stylesheet for decisions such as:

- brand-specific typography and colors
- page-specific layouts
- custom content components
- decorative effects
- unusual responsive behavior
- integration styles for third-party content

MiddleClass should remain the semantic foundation rather than the only stylesheet a site is allowed to use.

## Testing Customizations

After substantial customization, review:

- narrow and wide viewports
- automatic, explicit light, and explicit dark themes
- normal, hover, focus, active, and disabled states
- navigation, forms, buttons, tables, cards, notices, and dropdowns
- long headings, long links, and enlarged text
- keyboard focus visibility and color contrast

A customization is successful when it changes the site's presentation without weakening semantic structure, responsive behavior, or accessibility.

## Related Documentation

- [CSS variables](variables.md) lists every documented variable and default value.
- [Classes](classes.md) documents the public class API and supported markup.
- [Spacing](spacing.md) explains vertical rhythm and spacing ownership.
- [Sizing and units](sizing.md) explains the framework's unit policy.
- [Accessibility](accessibility.md) describes the accessibility baseline and author responsibilities.
