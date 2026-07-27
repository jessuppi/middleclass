# StyleWire

StyleWire is a lightweight, classless-first CSS framework for semantic static websites.

It gives plain HTML a clean responsive foundation, then adds a small set of layout and component classes for choices that semantic markup cannot express by itself.

## Goals

- Make ordinary semantic HTML look intentional.
- Work from one readable CSS file with no build step.
- Keep selectors understandable and easy to override.
- Keep the public class API small and deliberate.
- Support static hosting such as GitHub Pages and Cloudflare Pages.
- Avoid JavaScript, package managers, preprocessors, and rigid component markup structures.

## Usage

Copy `stylewire.css` into a site and link it from the document head:

```html
<link rel="stylesheet" href="/assets/stylewire.css">
```

A minimal page can use semantic HTML without component classes:

```html
<!doctype html>
<html lang="en">
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>Example</title>
	<link rel="stylesheet" href="stylewire.css">
</head>
<body>
	<header>
		<div class="container">
			<nav aria-label="Primary navigation">
				<ul>
					<li><strong>Example</strong></li>
					<li><a href="/about/">About</a></li>
				</ul>
			</nav>
		</div>
	</header>

	<main>
		<div class="container reading-width">
			<h1>Hello, world.</h1>
			<p>StyleWire handles the foundation while the document remains ordinary HTML.</p>
		</div>
	</main>
</body>
</html>
```

Open `index.html` to see the current elements and components together.

## Documentation

- [Architecture](docs/architecture.md) explains the classless-first model, limited class API, selector strategy, and framework boundaries.
- [Accessibility](docs/accessibility.md) describes the current accessibility baseline, author responsibilities, and basic testing expectations.
- [Sizing and units](docs/sizing.md) explains when StyleWire uses `rem`, `em`, `px`, unitless values, and responsive layout units.
- [CSS variables](docs/variables.md) documents the reusable values available for framework customization.

## Public classes

StyleWire intentionally keeps its class API small.

### Layout

- `.container` centers content within the main site width and responsive gutters.
- `.reading-width` limits long-form content to a comfortable line length.
- `.stack` arranges children vertically with consistent spacing.
- `.cluster` wraps related inline items such as buttons or navigation controls.
- `.columns` creates responsive equal-width columns.

Component spacing can be adjusted locally with custom properties:

```html
<div class="columns" style="--sw-columns-space: 2rem;">
	...
</div>
```

### Components

- `.button` gives a link button presentation.
- `.secondary` and `.outline` provide alternate button styles.
- `.card` creates a contained surface.
- `.notice` creates a highlighted message.
- `.success`, `.warning`, and `.danger` change a notice status accent.
- `.table-wrap` allows wide tables to scroll on narrow screens.
- `.muted` uses the secondary text color.
- `.screen-reader-text` visually hides accessible text.

## Customization

Override variables after loading StyleWire:

```css
:root {
	--sw-content-width: 80rem;
	--sw-reading-width: 44rem;
	--sw-radius: 0.25rem;
}
```

Color overrides require theme-aware selectors. See [CSS variables](docs/variables.md) for examples.

All public custom properties use the `--sw-` prefix.

## Color themes

StyleWire follows the operating system color preference by default.

Set an explicit theme on the root element when a site needs to override that behavior:

```html
<html lang="en" data-theme="light">
```

```html
<html lang="en" data-theme="dark">
```

StyleWire does not include a theme toggle because interactive behavior belongs to the site, not the CSS framework.

## Browser approach

StyleWire targets modern browsers without transpilation or compatibility bundles. The source stays readable and uses progressive CSS features that fail safely where practical.

## Project scope

StyleWire is a CSS foundation, not an application framework. The project does not plan to include:

- JavaScript widgets
- utility-class generation
- CSS preprocessors
- package-manager requirements
- framework adapters
- icon libraries
- bundled fonts
- application state or routing

## Versioning

StyleWire follows semantic versioning. The version appears in the stylesheet header and changelog.

Before 1.0, documented classes, variables, theme behavior, and semantic element styling may change between minor releases.

## License

StyleWire is available under the MIT License.
