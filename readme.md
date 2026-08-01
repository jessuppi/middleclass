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
- [Scope](docs/scope.md) defines what MiddleClass is intended to provide and what remains outside the project.
- [Customization](docs/customization.md) explains the recommended override workflow, themes, typography, spacing, and site-specific styling.
- [Classes](docs/classes.md) is the canonical reference for every supported public class, its expected markup, and important limitations.
- [Accessibility](docs/accessibility.md) describes the current accessibility baseline, author responsibilities, and basic testing expectations.
- [Sizing and units](docs/sizing.md) explains when MiddleClass uses `rem`, `em`, `px`, unitless values, and responsive layout units.
- [Spacing](docs/spacing.md) defines the vertical rhythm, structural spacing ownership, padded component edges, layout gaps, and intentional exceptions.
- [CSS variables](docs/variables.md) documents the reusable values available for framework customization.

## Browser approach

MiddleClass targets modern browsers without transpilation or compatibility bundles. The source stays readable and uses progressive CSS features that fail safely where practical.

## Versioning

MiddleClass follows semantic versioning. The version appears in the stylesheet header and changelog.

Before 1.0, documented classes, variables, theme behavior, and semantic element styling may change between minor releases.

Release tags use the plain numeric version, such as `0.1.0`, without a `v` prefix.

## License

MiddleClass is available under the MIT License. The embedded Font Awesome dropdown chevron retains its upstream license and attribution in the stylesheet and [Third-party notices](licenses/notice.md).
