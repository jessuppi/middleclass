# Releases

MiddleClass is distributed as a single local stylesheet, `middleclass.css`. Adopting sites choose when to copy a newer version; there is no package manager, build process, automatic update channel, or official CDN requirement.

## Versioning and Compatibility

The current project is **pre-1.0** and uses numbered releases (for example, `0.4.6`). As documented in [Architecture](architecture.md), its public classes, CSS variables, theme attributes, and semantic element behavior may change between minor releases. Do **not** interpret pre-1.0 version numbers as a guarantee of strict semantic-versioning compatibility.

- Keep changes deliberate, limited in scope, and documented in [Changelog](../changelog.md).
- Identify visible behavior changes, renamed or removed classes, and changed variables so adopters can evaluate upgrades.
- A CSS-only fix can still affect existing layouts; do not assume a small version increment implies zero integration work.
- Updates confined to demo copy, SEO, documentation, or repo administration are **not** new framework features and ordinarily do not require a stylesheet version bump.

This guide describes the release process to follow, not an assertion that historical releases passed every item below.

## Maintainer Checklist

When publishing an updated framework stylesheet:

1. Review the proposed change against [Scope](scope.md), [Architecture](architecture.md), and the supported [Classes](classes.md) and [CSS variables](variables.md).
2. Check the stylesheet's copyright/license header, source notices, and any third-party attribution implications; retain required notices. See [Attribution](attribution.md) for the distinction between bundled and demo-only assets.
3. Run the manual checks in [Testing](testing.md), especially affected elements, themes, viewports, and browsers.
4. Select the next version deliberately. Keep the version comment in `middleclass.css`, the demo's download label, and the demo's `SoftwareSourceCode` structured-data `version` consistent when they describe a released CSS version.
5. Add a concise entry to [Changelog](../changelog.md) identifying notable changes and possible compatibility effects.
6. Update relevant user-facing documentation for changed public behavior.
7. Confirm the demo presents and links to the intended stylesheet. If publishing a Git tag or GitHub release, ensure it identifies the intended code version.

Documentation edits and release-related file changes must follow the repository's normal review and commit practices. A GitHub Actions run is not a prerequisite for releasing the CSS.

## How Adopting Sites Upgrade

1. Note the site's current local MiddleClass version, if recorded.
2. Read changelog entries between that version and the proposed new version.
3. Replace the site's **local copy** of `middleclass.css` with the intended release.
4. Keep site-specific overrides in a separate stylesheet loaded afterward; recheck any overrides of public variables, component behavior, or semantic defaults.
5. Check the site's own pages at mobile and desktop widths, in light/dark modes, and with keyboard navigation. Follow [Troubleshooting](troubleshooting.md) if styling changes unexpectedly.

Do not point production sites at the GitHub raw file or the demo URL as a substitute for a managed local asset. The demo's page metadata, tests, and marketing content are not part of the distributed CSS.

## What Counts as Core

`middleclass.css` is the consumable framework. The demo `index.html`, repository docs, images, metadata, and changelog explain or demonstrate it but are not automatically installed into adopting websites. A change to those support files does not by itself change the public CSS API.
