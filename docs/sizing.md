# Sizing and Units

MiddleClass uses a small, predictable sizing policy rather than forcing one CSS unit everywhere.

This document describes the current framework approach. The policy may evolve, but unit changes should always be deliberate and based on the behavior a value needs.

## General Policy

Use:

- `rem` for root-relative typography, spacing, component dimensions, widths, radii, and breakpoints
- `em` when a value should scale with the font size of a particular element
- `px` for fixed visual details such as hairline borders, focus outlines, and accessibility mechanics
- unitless values where CSS defines proportional behavior, especially `line-height` and zero
- `%`, viewport units, `fr`, and CSS math functions when sizing must respond to available space

MiddleClass does not ban any valid CSS unit. It chooses units according to what each dimension should follow.

## Why MiddleClass Uses `rem`

A `rem` value is relative to the root `<html>` font size. It does not compound when components are nested, so spacing and typography remain predictable throughout a page.

```css
.card {
	padding: 1.5rem;
}
```

The card padding remains tied to the root font size regardless of the font size inherited by the card.

MiddleClass does not set a pixel font size on `<html>`. This allows browser and user font-size preferences to remain effective.

Common uses for `rem` include:

- font sizes
- spacing variables
- component heights and widths
- content-width limits
- border radii
- media-query breakpoints

## When to Use `em`

For most properties, an `em` value is relative to the computed font size of the element where it is used. This is useful when a detail should grow or shrink with a particular component.

```css
.badge {
	padding: 0.25em 0.5em;
}
```

A larger badge font will automatically produce proportionally larger badge padding.

When `em` is used for the `font-size` property itself, it is relative to the inherited font size from the parent rather than the element's final computed font size.

MiddleClass also uses `em` for small typographic details that should follow nearby text, such as underline offsets and inline-code sizing.

Avoid using `em` for the main spacing system. Nested font-size changes can make `em` dimensions compound and become difficult to predict.

## When to Use `px`

Pixels remain appropriate for details that should stay visually fixed.

```css
:root {
	--mc-border-width: 1px;
}

:focus-visible {
	outline: 3px solid var(--mc-focus);
}
```

Typical `px` uses include:

- one-pixel borders
- focus-outline thickness and offset
- small shadows
- implementation values used to visually hide accessible text

MiddleClass does not use `px` for the general spacing or typography scales. Replacing every pixel value with a relative unit would reduce clarity without improving accessibility.

## Borders and Decorative Accents

Not every visible edge serves the same purpose.

Use `px` for hairline borders that should remain visually thin:

```css
.card {
	border: 1px solid var(--mc-border);
}
```

Use `rem` or `em` for wider decorative accents that should scale with the interface or component:

```css
.notice {
	border-inline-start: 0.25rem solid var(--mc-accent);
}
```

A notice rail is a component dimension, not a hairline border, so a scalable unit is intentional.

## Unitless Values

Use unitless values where CSS defines proportional behavior.

```css
body {
	line-height: 1.6;
}
```

A unitless `line-height` scales with each element's own font size and inherits cleanly. Using `1.6rem` would force the same absolute line height onto differently sized text.

Zero should normally remain unitless:

```css
figure {
	margin: 0;
}
```

Do not add units to zero unless a particular CSS function or syntax requires them.

## Responsive and Layout Units

Use percentages and viewport-relative units when a dimension should respond to its container or the viewport.

MiddleClass combines relative units with CSS math functions when values need limits:

```css
:root {
	--mc-gutter: clamp(1rem, 4vw, 2rem);
}
```

The gutter grows with the viewport but never becomes smaller than `1rem` or larger than `2rem`.

Useful responsive tools include:

- `%` for dimensions relative to a containing block
- `vw` and `vh` for dimensions relative to the viewport
- `svh`, `lvh`, and `dvh` when mobile viewport behavior requires a more specific height model
- `fr` for distributing available space in CSS Grid
- `min()`, `max()`, and `clamp()` for bounded responsive values
- `minmax()` for flexible grid tracks

Traditional `vh` remains valid when its browser behavior is acceptable. Prefer `svh`, `lvh`, or `dvh` when browser interface changes on mobile could materially affect the layout.

## Breakpoints

MiddleClass uses `rem` for media-query breakpoints:

```css
@media (max-width: 40rem) {
	/* narrow-screen rules */
}
```

This keeps breakpoints aligned with the document's root scale instead of treating them as unrelated fixed pixels.

## Default Spacing Scale

MiddleClass uses a root-relative spacing scale:

| Variable | Value | Approximate size at a 16px root |
| --- | ---: | ---: |
| `--mc-space-1` | `0.25rem` | 4px |
| `--mc-space-2` | `0.5rem` | 8px |
| `--mc-space-3` | `0.75rem` | 12px |
| `--mc-space-4` | `1rem` | 16px |
| `--mc-space-5` | `1.5rem` | 24px |
| `--mc-space-6` | `2rem` | 32px |
| `--mc-space-7` | `3rem` | 48px |
| `--mc-space-8` | `4rem` | 64px |

The pixel column is only a familiar reference. Actual rendered sizes follow the user's root font size.

The spacing scale defines available values. [Spacing](spacing.md) defines how MiddleClass applies those values to document flow, structural elements, layout classes, padded components, and intentional exceptions.

## Accessibility Exceptions

Some accessibility techniques use tiny fixed dimensions for implementation rather than visual design.

For example, visually hidden text may use `1px` dimensions and a negative pixel margin while remaining available to assistive technology. These values are intentional exceptions and should not be converted to the spacing scale.

## Practical Review Rule

When adding or reviewing MiddleClass CSS, ask what the dimension should follow:

- The document's root scale: use `rem`
- The current component's text: use `em`
- A fixed visual edge or implementation detail: use `px`
- Proportional inherited behavior: use a unitless value
- The available layout space: use `%`, viewport units, `fr`, or CSS math functions

Do not convert units mechanically. Choose the unit that matches the intended behavior.
