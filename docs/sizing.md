# Sizing and Units

StyleWire uses a small, predictable sizing policy rather than forcing one CSS unit everywhere.

## General Policy

Use:

- `rem` for typography, spacing, component dimensions, widths, and radii
- `em` when a value should scale with the font size of its own element
- `px` for fixed visual details such as thin borders and focus outlines
- `%`, viewport units, and `clamp()` when sizing must respond to available space

This keeps the framework scalable without giving up precise visual control.

## Why StyleWire Uses `rem`

A `rem` value is relative to the root `<html>` font size. It does not compound when components are nested, so spacing and typography remain predictable throughout a page.

```css
.card {
	padding: 1.5rem;
}
```

The card padding remains tied to the root font size regardless of the font size inherited by the card.

StyleWire does not set a pixel font size on `<html>`. This allows browser and user font-size preferences to remain effective.

## When to Use `em`

An `em` value is relative to the font size of the element where it is used. This is useful when a detail should grow or shrink with a particular component.

```css
.badge {
	padding: 0.25em 0.5em;
}
```

A larger badge font will automatically produce proportionally larger badge padding.

Avoid using `em` for the main spacing system. Nested font-size changes can make `em` dimensions compound and become difficult to predict.

## When to Use `px`

Pixels remain appropriate for details that should stay visually fixed.

```css
:root {
	--sw-border-width: 1px;
}

:focus-visible {
	outline: 3px solid var(--sw-focus);
}
```

StyleWire does not ban pixels. Replacing every pixel value with a relative unit would reduce clarity without improving accessibility.

## Responsive Units

Use percentages and viewport-relative units when a dimension should respond to its container or the viewport.

StyleWire combines these units with `clamp()` where a value needs minimum and maximum limits:

```css
:root {
	--sw-gutter: clamp(1rem, 4vw, 2rem);
}
```

The gutter grows with the viewport but never becomes smaller than `1rem` or larger than `2rem`.

## Default Spacing Scale

StyleWire uses a root-relative spacing scale:

| Token | Value | Approximate size at a 16px root |
| --- | ---: | ---: |
| `--sw-space-1` | `0.25rem` | 4px |
| `--sw-space-2` | `0.5rem` | 8px |
| `--sw-space-3` | `0.75rem` | 12px |
| `--sw-space-4` | `1rem` | 16px |
| `--sw-space-5` | `1.5rem` | 24px |
| `--sw-space-6` | `2rem` | 32px |
| `--sw-space-7` | `3rem` | 48px |
| `--sw-space-8` | `4rem` | 64px |

The pixel column is only a familiar reference. Actual rendered sizes follow the user's root font size.

## Practical Rule

When adding or reviewing StyleWire CSS, ask what the dimension should follow:

- The document's root scale: use `rem`
- The current component's text: use `em`
- A fixed visual edge: use `px`
- The available layout space: use `%`, viewport units, or `clamp()`

Do not convert units mechanically. Choose the unit that matches the intended behavior.