# MiddleClass

MiddleClass is a lightweight, classless-first CSS framework for semantic static websites. It gives common HTML elements, navigation, forms, tables, and content structures clean, responsive defaults before any component classes are added.

The framework is distributed as one readable CSS file with no build step, package manager, preprocessor, or JavaScript dependency. A small public class API handles common layout and presentation choices that semantic markup cannot express by itself.

MiddleClass can be used for blogs, documentation, landing pages, small business websites, and other content-focused projects, but its primary audience is smaller sites deployed with services such as GitHub Pages or Cloudflare Workers. It works without customization, while projects that need their own design can load an optional `style.css` after `middleclass.css` to override variables, element styles, or public classes.

## Usage

Copy [`middleclass.css`](middleclass.css) into your project and link the local file from the document head:

```html
<link rel="stylesheet" href="/assets/middleclass.css">
```

Host the stylesheet with your project rather than linking to GitHub, a raw GitHub URL, or the demo site. MiddleClass has no official CDN yet; a supported option may be introduced later through a provider such as Cloudflare, but local hosting is the supported approach for now.

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

The [demo site](https://jessuppi.github.io/middleclass/) is the quickest way to see MiddleClass styles, public classes, forms, themes, and responsive behavior together. The documents below cover the framework's design, scope, supported API, customization options, and implementation details.

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
