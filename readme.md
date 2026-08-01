# MiddleClass

## Description

MiddleClass is a lightweight, classless-first CSS framework for semantic static websites. It gives ordinary HTML a clean, responsive foundation before any component classes are added.

A small public class API handles layout and presentation choices that semantic markup cannot express by itself. The framework is distributed as one readable CSS file with no build step, package manager, preprocessor, JavaScript dependency, or rigid component structure.

MiddleClass is designed for straightforward static hosting and easy site-level customization through understandable selectors, documented variables, and a deliberately limited public API.

**Live demo:** [jessuppi.github.io/middleclass](https://jessuppi.github.io/middleclass/)

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

| Document | Description |
| --- | --- |
| [Architecture](docs/architecture.md) | Explains the classless-first model, limited class API, selector strategy, browser approach, and framework boundaries. |
| [Scope](docs/scope.md) | Defines what MiddleClass is intended to provide and what remains outside the project. |
| [Customization](docs/customization.md) | Explains the recommended override workflow, themes, typography, spacing, and site-specific styling. |
| [Classes](docs/classes.md) | The canonical reference for every supported public class, its expected markup, and important limitations. |
| [Accessibility](docs/accessibility.md) | Describes the current accessibility baseline, author responsibilities, and basic testing expectations. |
| [Sizing and units](docs/sizing.md) | Explains when MiddleClass uses `rem`, `em`, `px`, unitless values, and responsive layout units. |
| [Spacing](docs/spacing.md) | Defines the vertical rhythm, structural spacing ownership, padded component edges, layout gaps, and intentional exceptions. |
| [CSS variables](docs/variables.md) | Documents the reusable values available for framework customization. |

## License

MiddleClass is available under the MIT License. The embedded Font Awesome dropdown chevron retains its upstream license and attribution in the stylesheet and [Third-party notices](licenses/notice.md).
