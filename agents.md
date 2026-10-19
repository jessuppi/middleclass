# Agent Instructions

These instructions apply to the entire MiddleClass repository. Consult the existing documentation before making changes.

## Project

- MiddleClass is a lightweight, classless-first CSS framework for semantic static websites.
- The distributable framework is the root-level `middleclass.css`: one readable stylesheet, with no JavaScript, package manager, preprocessor, or build requirement.
- `index.html` is the GitHub Pages demo and manual regression fixture, not part of the CSS API.
- Keep demo-only markup, metadata, SEO, imagery, and site-specific presentation separate from the core framework.
- Prefer native HTML, a small intentional public class API, accessible defaults, low selector specificity, and straightforward customization.

## Documentation

- Read [Scope](docs/scope.md) and [Architecture](docs/architecture.md) before proposing new framework features.
- Use [Classes](docs/classes.md) and [CSS variables](docs/variables.md) as the public API references.
- Follow [Customization](docs/customization.md), [Spacing](docs/spacing.md), and [Sizing and units](docs/sizing.md) when changing styling behavior.
- Review [Accessibility](docs/accessibility.md), [Browser Support](docs/browser-support.md), and [Localization](docs/localization.md) when relevant.
- Use [Testing](docs/testing.md) for the manual regression checklist and [Releases](docs/releases.md) with [Changelog](changelog.md) for release-related updates.
- [SEO](docs/seo.md) describes demo-specific metadata and site-owner responsibilities; SEO tooling is not part of MiddleClass core.

## Editing and Verification

- Make the smallest required changes; do not introduce unrelated formatting, cleanup, refactoring, dependencies, or features.
- Keep site-specific styling in a site's own stylesheet instead of expanding `middleclass.css`.
- Do not add public classes or variables unless they meet the admission criteria in the architecture guide.
- For CSS behavior changes, review affected documentation, the demo, responsive layouts, themes, keyboard focus, native controls, and the regression section. Test browsers when available, but never claim unperformed checks.
- Keep required third-party attribution and license notices intact.
- Update the changelog and version references when releasing a new stylesheet version. Keep the stylesheet header, demo download label, and demo structured-data version consistent. Documentation-only or demo-only edits do not require a CSS version bump.

## GitHub Changes

- Work directly on the default `master` branch unless explicitly instructed otherwise.
- **Exactly one changed file per commit.** Group related edits within that file into one commit; commit different files separately.
- Before each commit, verify that it modifies only the intended single file. If a one-file intermediate commit would break the build or deployment, stop and explain the dependency first.
- Use normal direct file updates and commits only. Do not create branches or pull requests, or squash, amend, force-push, or rewrite history.
- Never use workflows, GitHub Actions, CI jobs, Git trees, Git blobs, patches, or temporary automation to edit or commit repository files.
- Do not trigger a deployment or workflow unless specifically asked, and never use one to apply code changes.
- Report each commit separately with its SHA, message, and exact file changed.
