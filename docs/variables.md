# CSS Variables

MiddleClass uses CSS variables to store reusable framework values such as colors, spacing, widths, radii, and typography settings.

The formal CSS term is custom properties. This documentation uses CSS variables because it is the more familiar name.

## Basic Use

A variable has a name and a value:

```css
:root {
	--mc-accent: #175cd3;
}
```

The value is reused with `var()`:

```css
a {
	color: var(--mc-accent);
}
```

Changing the variable changes every rule that uses it.

## Prefix

All public MiddleClass variables use the `--mc-` prefix. This reduces naming conflicts with site-specific CSS and other libraries.

Site variables should use a different prefix or an unambiguous project-specific name.

## Public API Status

The variables documented here are the current intended customization points for MiddleClass.

MiddleClass is pre-1.0, so documented variables may still change between minor releases. Renames, removals, and behavior changes should remain deliberate and be recorded in the changelog.

## Value Type Guidance

Current variables expect values in these general categories:

| Variable group | Expected value |
| --- | --- |
| Font-family variables | A valid CSS font-family list |
| Font-size, width, gutter, radius, border-width, spacing, and component-gap variables | A valid CSS length or math expression that resolves to a length |
| `--mc-line-height` | A unitless number |
| Color variables | A valid CSS color |

Overrides should preserve the existing value category of each variable.

## Overriding Variables

Load MiddleClass first, then define overrides in the site's own stylesheet:

```css
:root {
	--mc-content-width: 80rem;
	--mc-reading-width: 44rem;
	--mc-radius: 0.25rem;
}
```

Color variables require theme-aware selectors because MiddleClass's theme rules are more specific than a plain `:root` rule. To customize colors used by automatic dark mode, match the framework selector:

```css
@media (prefers-color-scheme: dark) {
	:root:not([data-theme="light"]) {
		--mc-accent: #b69cff;
		--mc-accent-hover: #d1c1ff;
	}
}
```

Use `[data-theme="light"]` and `[data-theme="dark"]` for explicit theme overrides, as shown in the theme section below.

There is normally no need to edit `middleclass.css` directly.

## Typography Variables

| Variable | Default | Purpose |
| --- | --- | --- |
| `--mc-font-sans` | System sans-serif stack | Default text font |
| `--mc-font-mono` | System monospace stack | Code and keyboard text |
| `--mc-font-size` | `1rem` | Default body font size |
| `--mc-line-height` | `1.6` | Default body line height |

## Layout Variables

| Variable | Default | Purpose |
| --- | --- | --- |
| `--mc-content-width` | `72rem` | Maximum main container width |
| `--mc-reading-width` | `48rem` | Maximum long-form reading width |
| `--mc-gutter` | `clamp(1rem, 4vw, 2rem)` | Responsive page gutter |
| `--mc-radius` | `0.5rem` | Standard component radius |
| `--mc-radius-small` | `0.25rem` | Smaller control radius |
| `--mc-border-width` | `1px` | Standard hairline border width |

## Spacing Variables

| Variable | Default |
| --- | ---: |
| `--mc-space-1` | `0.25rem` |
| `--mc-space-2` | `0.5rem` |
| `--mc-space-3` | `0.75rem` |
| `--mc-space-4` | `1rem` |
| `--mc-space-5` | `1.5rem` |
| `--mc-space-6` | `2rem` |
| `--mc-space-7` | `3rem` |
| `--mc-space-8` | `4rem` |

Use the existing spacing scale before adding unrelated one-off spacing values. See [Sizing and units](sizing.md) for the unit policy behind this scale.

## Color Variables

| Variable | Light default | Dark default | Purpose |
| --- | --- | --- | --- |
| `--mc-background` | `#ffffff` | `#11161c` | Page and form-control background |
| `--mc-surface` | `#f5f7f9` | `#19212a` | Standard component surface |
| `--mc-surface-strong` | `#e8edf2` | `#25313d` | Stronger secondary surface |
| `--mc-text` | `#18212b` | `#edf2f7` | Main text color |
| `--mc-text-muted` | `#5d6875` | `#aab5c0` | Secondary text color |
| `--mc-border` | `#7b8a99` | `#607080` | Standard border color |
| `--mc-accent` | `#175cd3` | `#78a9ff` | Primary interactive accent |
| `--mc-accent-hover` | `#114aa9` | `#a6c5ff` | Hover-state accent |
| `--mc-accent-text` | `#ffffff` | `#101820` | Text shown on the accent color |
| `--mc-focus` | `#9a6700` | `#ffd166` | Keyboard focus outline |
| `--mc-code-background` | `#eef2f6` | `#202a34` | Code background |
| `--mc-success` | `#217a3c` | `#68c77b` | Success status accent |
| `--mc-warning` | `#8a5a00` | `#f0bd5a` | Warning status accent |
| `--mc-danger` | `#b42318` | `#ff8b82` | Danger status accent |

## Color Pairing and Contrast

Color variables work as related groups rather than isolated values. When overriding colors:

- review `--mc-accent`, `--mc-accent-hover`, and `--mc-accent-text` together
- verify `--mc-text` and `--mc-text-muted` against the page and surface backgrounds
- keep `--mc-border` visible against every surface where it appears
- ensure `--mc-focus` remains clearly visible around interactive elements
- review success, warning, and danger accents in both light and dark themes

Test normal, hover, focus, and disabled states after changing a color group. A color that looks acceptable by itself may not provide sufficient contrast when used for text, backgrounds, borders, or focus indicators.

MiddleClass provides balanced defaults, but a site that overrides color variables is responsible for preserving accessible contrast in every supported theme.

## Light and Dark Themes

Color variables change with the active color theme. Non-color variables remain shared.

MiddleClass follows the operating system preference by default. A site can force a theme with `data-theme="light"` or `data-theme="dark"` on the root element.

Theme-specific overrides should target the same selectors:

```css
[data-theme="light"] {
	--mc-accent: #6b3fc8;
	--mc-accent-hover: #5630a7;
}

[data-theme="dark"] {
	--mc-accent: #b69cff;
	--mc-accent-hover: #d1c1ff;
}
```

When automatic system theming must also use custom dark colors, override the variables inside a matching `prefers-color-scheme` media query as shown above.

## Component Variables

A few variables customize one layout instance rather than the entire framework:

- `--mc-stack-space` controls the gap inside `.stack`
- `--mc-cluster-space` controls the gap inside `.cluster`
- `--mc-columns-space` controls the gap inside `.columns`

They can be set directly on a component:

```html
<div class="columns" style="--mc-columns-space: 2rem;">
	...
</div>
```

Each component variable falls back to the normal MiddleClass spacing scale when it is not set.

Because CSS variables inherit, setting a component variable on a shared ancestor can affect every nested matching component. Set the variable directly on a specific `.stack`, `.cluster`, or `.columns` element when only one instance should change.

## Scope and Inheritance

Variables inherit through the document. A variable set on `:root` applies globally, while a variable set on a particular element applies to that element and its descendants.

```css
.special-section {
	--mc-accent: #9b2c2c;
}
```

Links and buttons inside `.special-section` use that accent without changing the rest of the page.

Inheritance also means that an override may reach nested components unless a more specific descendant value replaces it. Scope overrides as narrowly as the intended effect requires.

## When to Add a Variable

Add a public variable when a value is:

- reused in multiple places
- an intentional part of the framework's visual system
- reasonably useful for sites to customize
- stable enough to support as public API

Do not create a variable for every numeric or color value. A one-off implementation detail is usually clearer as a normal property value.

## Practical Rule

Use variables for shared choices that users may need to change. Use ordinary CSS values for isolated implementation details.
