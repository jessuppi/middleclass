# Branding

MiddleClass uses a compact `.MC` monogram as its primary logo. The mark is intentionally simple, geometric, and suitable for headers, favicons, documentation, and other small web surfaces.

Primary asset:

`assets/middleclass-logo.svg`

## Logo Construction

The logo consists of three elements:

- a blue period representing CSS class syntax
- a dark `M`
- a dark `C`

The standalone `MiddleClass` wordmark is not part of the primary logo. Use the `.MC` mark by itself.

The current SVG is a true vector asset built from SVG circle and path geometry. Do not replace it with an embedded PNG, JPEG, or other raster image.

## Geometry

The geometry is intentionally normalized:

- `M`: 92 units wide × 78 units high
- `C`: 92 units wide × 78 units high
- both letters share the same top and bottom bounds
- both letters bottom-align at `y=126`
- the blue period also bottoms at `y=126`
- period center: `y=111`
- period radius: `15`

The equal letter width is intentional. The `C` is wider than a conventional typographic C so that the two-letter monogram has balanced geometric proportions.

Do not independently resize, stretch, raise, or lower the M, C, or period. If the logo is resized, scale the complete SVG uniformly.

## Colors

The primary colors are:

- period: `#2563EB`
- letters: `#0F172A`

Keep these colors for the standard logo unless a deliberate alternate branding variant is introduced later.

## SVG Canvas

The primary asset currently uses:

```svg
viewBox="20 45 245 90"
```

The viewBox is kept tight around the artwork so the logo fills its available canvas without excessive empty space.

When embedding the logo, size the SVG through its rendered width or height rather than editing its internal coordinates.

## Web Usage

Preferred HTML:

```html
<img src="/assets/middleclass-logo.svg" alt="MiddleClass">
```

When the logo is already inside a link whose purpose is clear from surrounding context, keep the accessible name concise and avoid adding duplicate visible branding text purely for labeling.

The SVG should remain the canonical source for web use. Raster exports may be created when a platform requires them, but they should be generated from the SVG rather than becoming the source artwork.

## Favicon and Small Sizes

The `.MC` mark is designed to remain recognizable at small sizes. For favicon or app-icon variants:

- preserve the same basic geometry
- preserve the shared bottom alignment
- preserve equal M and C dimensions
- avoid adding the full `MiddleClass` wordmark
- avoid decorative effects, gradients, shadows, or extra shapes

If a very small favicon requires a specialized crop or simplified export, keep the primary SVG unchanged and create a separate derived asset.

## Graphics Direction

Future MiddleClass graphics should follow the same visual character as the logo:

- clean
- modern
- geometric
- minimal
- web-oriented
- low-detail
- easy to recognize at small sizes

Avoid ornamental typography, glossy effects, faux-3D treatments, unnecessary gradients, and visual clutter. The branding should feel like a lightweight developer tool rather than a corporate or decorative identity.
