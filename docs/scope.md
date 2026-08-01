# Scope

MiddleClass provides a clean, responsive CSS foundation for semantic static websites.

The project is intended to:

- make ordinary semantic HTML look intentional without requiring component classes
- remain one readable CSS file with no build step
- keep selectors understandable and easy for site stylesheets to override
- provide a small, deliberate public class API for layout and presentation choices that HTML cannot express by itself
- support static hosting such as GitHub Pages and Cloudflare Pages
- avoid unnecessary tooling, dependencies, and rigid component markup structures

## Boundaries

MiddleClass is a CSS foundation, not an application framework. The project does not plan to include:

- JavaScript widgets
- utility-class generation
- CSS preprocessors
- package-manager requirements
- framework adapters
- general-purpose icon libraries
- bundled fonts
- application state or routing

The embedded Font Awesome dropdown chevron is a narrowly scoped component affordance, not an author-facing icon collection.
