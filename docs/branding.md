# Branding

MiddleClass uses a compact `.MC` monogram as its primary logo. The mark is intentionally simple, geometric, and suitable for headers, documentation, and other web surfaces.

Primary logo asset:

`assets/middleclass-logo.svg`

Favicon asset:

`assets/middleclass-icon.svg`

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

- period and favicon dot: `#2563EB`
- letters: `#0F172A`

Keep these colors for the standard logo and icon unless a deliberate alternate branding variant is introduced later.

## SVG Canvas

The primary logo asset currently uses:

```svg
viewBox="20 45 245 90"
```

The viewBox is kept tight around the artwork so the logo fills its available canvas without excessive empty space.

When embedding the logo, size the SVG through its rendered width or height rather than editing its internal coordinates.

## Web Usage

Preferred logo HTML:

```html
<img src="/assets/middleclass-logo.svg" alt="MiddleClass">
```

When the logo is already inside a link whose purpose is clear from surrounding context, keep the accessible name concise and avoid adding duplicate visible branding text purely for labeling.

The SVG should remain the canonical source for web use. Raster exports may be created when a platform requires them, but they should be generated from the SVG rather than becoming the source artwork.

## Favicon

The favicon intentionally uses only the blue class dot rather than the full `.MC` mark. This keeps the icon simple and legible at very small browser-tab sizes.

The canonical favicon asset is:

`assets/middleclass-icon.svg`

Its geometry is:

- square `128 × 128` viewBox
- circle centered at `64,64`
- circle radius `48`
- circle diameter `96`
- `16` units of padding on every side
- `12.5%` padding per side
- transparent background
- brand blue `#2563EB`

The favicon should remain a pure SVG circle with no letters, wordmark, gradients, shadows, raster data, fonts, scripts, or external dependencies.

Preferred HTML:

```html
<link rel="icon" href="assets/middleclass-icon.svg" type="image/svg+xml" sizes="any">
```

Keep the dot perfectly centered. If additional favicon formats are ever required for a specific platform, derive them from this SVG while keeping `middleclass-icon.svg` as the canonical source.

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
