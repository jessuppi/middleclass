# MiddleClass

MiddleClass is a lightweight, classless-first CSS framework for semantic static websites. It gives ordinary HTML a clean, responsive foundation before any component classes are added.

A small public class API handles layout and presentation choices that semantic markup cannot express by itself. The framework is distributed as one readable CSS file with no build step, package manager, preprocessor, JavaScript dependency, or rigid component structure.

MiddleClass is designed for straightforward static hosting and easy site-level customization through understandable selectors, documented variables, and a deliberately limited public API.

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

## Documentation

| Document | Description |
| --- | --- |
| [Architecture](docs/architecture.md) | Explains the classless-first model, why the limited class layer exists, class admission rules, selector strategy, stylesheet organization, public API boundaries, browser expectations, and criteria for evaluating new features. |
| [Scope](docs/scope.md) | Defines the framework's intended purpose and development goals, together with explicit boundaries around tooling, JavaScript, utility generation, fonts, icons, routing, and other application concerns. |
| [Customization](docs/customization.md) | Provides a practical guide to loading site styles, overriding global or scoped variables, changing typography, widths, spacing, colors, themes, component presentation, and testing the result. |
| [Classes](docs/classes.md) | Serves as the canonical reference for every supported public class, including its purpose, expected markup, compatible variants, local variables, behavior, limitations, and usage examples. |
| [Accessibility](docs/accessibility.md) | Describes the framework's accessibility baseline, the responsibilities that remain with site authors, component-specific considerations, and basic checks for semantics, focus, contrast, forms, and assistive technology. |
| [Sizing and units](docs/sizing.md) | Explains where and why MiddleClass uses `rem`, `em`, `px`, unitless values, percentages, viewport-aware expressions, and responsive layout units throughout the stylesheet. |
| [Spacing](docs/spacing.md) | Defines the vertical rhythm model, which elements own external spacing, how layout classes control internal gaps, how padded components trim their edges, and where intentional exceptions apply. |
| [CSS variables](docs/variables.md) | Lists the documented customization variables, default values, expected value types, theme-aware color overrides, component-level variables, inheritance behavior, and guidance for extending the variable API. |

## License

MiddleClass is available under the MIT License. The embedded Font Awesome dropdown chevron retains its upstream license and attribution in the stylesheet and [Third-party notices](licenses/notice.md).
