# MiddleClass

MiddleClass is a lightweight, classless-first CSS framework for semantic static websites.

It gives plain HTML a clean responsive foundation, then adds a small set of layout and component classes for choices that semantic markup cannot express by itself.

**Live demo:** [jessuppi.github.io/middleclass](https://jessuppi.github.io/middleclass/)

## Goals

- Make ordinary semantic HTML look intentional.
- Work from one readable CSS file with no build step.
- Keep selectors understandable and easy to override.
- Keep the public class API small and deliberate.
- Support static hosting such as GitHub Pages and Cloudflare Pages.
- Avoid JavaScript, package managers, preprocessors, and rigid component markup structures.

## Usage

Download or copy [`middleclass.css`](middleclass.css) into a site and link it from the document head:

```html
<link rel="stylesheet" href="/assets/middleclass.css">
```

A minimal page can use semantic HTML without component classes:

```html
<!doctype html>
<html lang="en">
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>Example</title>
	<link rel="stylesheet" href="middleclass.css">
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
			<p>MiddleClass handles the foundation while the document remains ordinary HTML.</p>
		</div>
	</main>
</body>
</html>
```

Use the [live demonstration](https://jessuppi.github.io/middleclass/) as a visual reference for semantic elements, public classes, forms, vertical rhythm, themes, and responsive behavior.

## Documentation

- [Architecture](docs/architecture.md) explains the classless-first model, limited class API, selector strategy, and framework boundaries.
- [Classes](docs/classes.md) is the canonical reference for every supported public class, its expected markup, and important limitations.
- [Accessibility](docs/accessibility.md) describes the current accessibility baseline, author responsibilities, and basic testing expectations.
- [Sizing and units](docs/sizing.md) explains when MiddleClass uses `rem`, `em`, `px`, unitless values, and responsive layout units.
- [Spacing](docs/spacing.md) defines the vertical rhythm, structural spacing ownership, padded component edges, layout gaps, and intentional exceptions.
- [CSS variables](docs/variables.md) documents the reusable values available for framework customization.

## Public classes

MiddleClass intentionally keeps its public class API small:

- Layout: `.container`, `.reading-width`, `.stack`, `.cluster`, `.columns`, and `.push-end`
- Buttons and variants: `.button`, `.secondary`, and `.outline`
- Content components: `.card`, `.notice`, `.success`, `.warning`, `.danger`, `.dropdown`, `.dropdown-start`, and `.dropup`
- Supporting behavior: `.table-wrap`, `.muted`, and `.screen-reader-text`

See [Classes](docs/classes.md) for the complete usage reference. Semantic element defaults remain the foundation of the framework, and site-specific presentation should remain in the site's own stylesheet.

## Customization

Override variables after loading MiddleClass:

```css
:root {
	--mc-content-width: 80rem;
	--mc-reading-width: 44rem;
	--mc-radius: 0.25rem;
}
```

Color overrides require theme-aware selectors. See [CSS variables](docs/variables.md) for examples.

All public custom properties use the `--mc-` prefix.

Dropdowns use a Font Awesome chevron by default. A site can switch every dropdown to another bundled family with one root attribute:

```html
<html lang="en" data-mc-icon-family="material">
```

Supported dropdown chevron families are Font Awesome, Material Icons, Lucide, and Heroicons. The attribute may also be scoped to one section or dropdown, and `--mc-dropdown-chevron` accepts a custom image. See [CSS variables](docs/variables.md) for the complete API.

## Color themes

MiddleClass follows the operating system color preference by default.

Set an explicit theme on the root element when a site needs to override that behavior:

```html
<html lang="en" data-theme="light">
```

```html
<html lang="en" data-theme="dark">
```

MiddleClass does not include a theme toggle because interactive behavior belongs to the site, not the CSS framework.

## Browser approach

MiddleClass targets modern browsers without transpilation or compatibility bundles. The source stays readable and uses progressive CSS features that fail safely where practical.

## Project scope

MiddleClass is a CSS foundation, not an application framework. The project does not plan to include:

- JavaScript widgets
- utility-class generation
- CSS preprocessors
- package-manager requirements
- framework adapters
- general-purpose icon libraries
- bundled fonts
- application state or routing

The embedded dropdown chevrons are narrowly scoped component affordances, not an author-facing icon collection.

## Versioning

MiddleClass follows semantic versioning. The version appears in the stylesheet header and changelog.

Before 1.0, documented classes, variables, theme behavior, and semantic element styling may change between minor releases.

Release tags use the plain numeric version, such as `0.1.0`, without a `v` prefix.

## License

MiddleClass is available under the MIT License. Embedded dropdown chevrons retain their upstream licenses and attribution in [Third-party notices](third-party-notices.md).
