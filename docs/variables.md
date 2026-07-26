# CSS Variables

StyleWire uses CSS variables to store reusable framework values such as colors, spacing, widths, radii, and typography settings.

The formal CSS term is custom properties. This documentation uses CSS variables because it is the more familiar name.

## Basic Use

A variable has a name and a value:

```css
:root {
	--sw-accent: #175cd3;
}
```

The value is reused with `var()`:

```css
a {
	color: var(--sw-accent);
}
```

Changing the variable changes every rule that uses it.

## Prefix

All public StyleWire variables use the `--sw-` prefix. This reduces naming conflicts with site-specific CSS and other libraries.

Site variables should use a different prefix or an unambiguous project-specific name.

## Overriding Variables

Load StyleWire first, then define overrides in the site's own stylesheet:

```css
:root {
	--sw-content-width: 80rem;
	--sw-reading-width: 44rem;
	--sw-radius: 0.25rem;
}
```

Color variables require theme-aware selectors because StyleWire's theme rules are more specific than a plain `:root` rule. To customize colors used by automatic dark mode, match the framework selector:

```css
@media (prefers-color-scheme: dark) {
	:root:not([data-theme="light"]) {
		--sw-accent: #b69cff;
		--sw-accent-hover: #d1c1ff;
	}
}
```

Use `[data-theme="light"]` and `[data-theme="dark"]` for explicit theme overrides, as shown in the theme section below.

There is normally no need to edit `stylewire.css` directly.

## Typography Variables

| Variable | Default | Purpose |
| --- | --- | --- |
| `--sw-font-sans` | System sans-serif stack | Default text font |
| `--sw-font-mono` | System monospace stack | Code and keyboard text |
| `--sw-font-size` | `1rem` | Default body font size |
| `--sw-line-height` | `1.6` | Default body line height |

## Layout Variables

| Variable | Default | Purpose |
| --- | --- | --- |
| `--sw-content-width` | `72rem` | Maximum main container width |
| `--sw-reading-width` | `48rem` | Maximum long-form reading width |
| `--sw-gutter` | `clamp(1rem, 4vw, 2rem)` | Responsive page gutter |
| `--sw-radius` | `0.5rem` | Standard component radius |
| `--sw-radius-small` | `0.25rem` | Smaller control radius |
| `--sw-border-width` | `1px` | Standard hairline border width |

## Spacing Variables

| Variable | Default |
| --- | ---: |
| `--sw-space-1` | `0.25rem` |
| `--sw-space-2` | `0.5rem` |
| `--sw-space-3` | `0.75rem` |
| `--sw-space-4` | `1rem` |
| `--sw-space-5` | `1.5rem` |
| `--sw-space-6` | `2rem` |
| `--sw-space-7` | `3rem` |
| `--sw-space-8` | `4rem` |

Use the existing spacing scale before adding unrelated one-off spacing values. See [Sizing and units](sizing.md) for the unit policy behind this scale.

## Color Variables

| Variable | Light default | Dark default | Purpose |
| --- | --- | --- | --- |
| `--sw-background` | `#ffffff` | `#11161c` | Page and form-control background |
| `--sw-surface` | `#f5f7f9` | `#19212a` | Standard component surface |
| `--sw-surface-strong` | `#e8edf2` | `#25313d` | Stronger secondary surface |
| `--sw-text` | `#18212b` | `#edf2f7` | Main text color |
| `--sw-text-muted` | `#5d6875` | `#aab5c0` | Secondary text color |
| `--sw-border` | `#cfd7df` | `#3a4856` | Standard border color |
| `--sw-accent` | `#175cd3` | `#78a9ff` | Primary interactive accent |
| `--sw-accent-hover` | `#114aa9` | `#a6c5ff` | Hover-state accent |
| `--sw-accent-text` | `#ffffff` | `#101820` | Text shown on the accent color |
| `--sw-focus` | `#f4b400` | `#ffd166` | Keyboard focus outline |
| `--sw-code-background` | `#eef2f6` | `#202a34` | Code background |
| `--sw-success` | `#217a3c` | `#68c77b` | Success status accent |
| `--sw-warning` | `#8a5a00` | `#f0bd5a` | Warning status accent |
| `--sw-danger` | `#b42318` | `#ff8b82` | Danger status accent |

## Light and Dark Themes

Color variables change with the active color theme. Non-color variables remain shared.

StyleWire follows the operating system preference by default. A site can force a theme with `data-theme="light"` or `data-theme="dark"` on the root element.

Theme-specific overrides should target the same selectors:

```css
[data-theme="light"] {
	--sw-accent: #6b3fc8;
	--sw-accent-hover: #5630a7;
}

[data-theme="dark"] {
	--sw-accent: #b69cff;
	--sw-accent-hover: #d1c1ff;
}
```

When automatic system theming must also use custom dark colors, override the variables inside a matching `prefers-color-scheme` media query as shown above.

## Component Variables

A few variables customize one layout instance rather than the entire framework:

- `--sw-stack-space` controls the gap inside `.stack`
- `--sw-cluster-space` controls the gap inside `.cluster`
- `--sw-columns-space` controls the gap inside `.columns`

They can be set directly on a component:

```html
<div class="columns" style="--sw-columns-space: 2rem;">
	...
</div>
```

Each component variable falls back to the normal StyleWire spacing scale when it is not set.

## Scope and Inheritance

Variables inherit through the document. A variable set on `:root` applies globally, while a variable set on a particular element applies only to that element and its descendants.

```css
.special-section {
	--sw-accent: #9b2c2c;
}
```

Links and buttons inside `.special-section` use that accent without changing the rest of the page.

## When to Add a Variable

Add a public variable when a value is:

- reused in multiple places
- an intentional part of the framework's visual system
- reasonably useful for sites to customize
- stable enough to support as public API

Do not create a variable for every numeric or color value. A one-off implementation detail is usually clearer as a normal property value.

## Practical Rule

Use variables for shared choices that users may need to change. Use ordinary CSS values for isolated implementation details.
