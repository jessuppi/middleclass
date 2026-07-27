# Architecture

StyleWire is a lightweight, classless-first CSS framework for semantic static websites.

Its architecture gives ordinary HTML useful defaults while reserving a small optional class layer for layout and presentation choices that HTML semantics cannot express by themselves.

This document describes the current direction. Details may evolve, but changes should preserve the framework's simplicity, readability, and semantic foundation.

## Classless First

Classless-first means a useful document should look intentional before component classes are added.

StyleWire styles ordinary elements such as:

- headings, paragraphs, lists, and links
- navigation
- blockquotes, code, figures, and horizontal rules
- tables
- forms and native buttons
- details and summary elements

The framework should not require a special class merely to make a standard semantic element usable.

```html
<article>
	<h1>Release notes</h1>
	<p>The document remains ordinary HTML.</p>
	<button type="button">Continue</button>
</article>
```

Classless-first does not mean that every layout or component must be inferred from element names.

## Why Classes Still Exist

HTML describes meaning and document structure. It does not provide semantic elements for every common layout or visual role.

For example, HTML has no element whose meaning is:

- a centered maximum-width container
- a narrow reading column
- a wrapping row of related controls
- responsive equal-width columns
- a visually contained card
- a warning notice
- a secondary or outlined button

StyleWire uses a limited class API for these cases rather than attaching strong visual assumptions to generic elements such as `div`, `section`, or `article`.

```html
<div class="columns">
	<article class="card">...</article>
	<article class="card">...</article>
</div>
```

This keeps semantic HTML useful without forcing StyleWire to guess the author's intent.

## Class Admission Rules

A new public class should normally satisfy all of these conditions:

- It represents a common layout, component, state, or presentation concept.
- HTML does not already express the concept clearly by itself.
- The class is useful across unrelated sites rather than one specific page.
- Its name describes intent instead of a low-level CSS declaration.
- Its behavior can remain small, predictable, and easy to override.
- It is valuable enough to justify expanding the public API.

A class should not be added merely because one declaration is convenient to reuse.

StyleWire should avoid utility classes such as `.mt-4`, `.flex`, `.rounded`, or `.text-center`. Those classes expose individual declarations and encourage large class lists rather than readable semantic markup.

Page-specific names such as `.homepage-box` or `.pricing-blue-column` belong in the site's own stylesheet, not the framework.

## Current Class Layers

The current public class API has three narrow roles. A fourth role may emerge later if the API develops a genuinely distinct group, but the framework does not target a fixed number of layers.

### Layout

- `.container`
- `.reading-width`
- `.stack`
- `.cluster`
- `.columns`

### Components and Variants

- `.button`
- `.secondary`
- `.outline`
- `.card`
- `.notice`
- `.success`
- `.warning`
- `.danger`

### Supporting Behavior

- `.table-wrap`
- `.muted`
- `.screen-reader-text`

These classes are optional. Semantic element defaults remain the foundation of the framework.

## Selector Strategy

StyleWire keeps selectors understandable and intentionally low in specificity.

Use:

- element selectors for semantic defaults
- single classes for public layouts and components
- limited compound selectors for variants and states
- pseudo-classes for interaction states
- direct-child selectors only when immediate structure matters

Avoid:

- ID selectors
- deeply nested selectors
- long chains of classes
- selectors tied to one page's DOM structure
- unnecessary `!important` declarations

The `.screen-reader-text` accessibility utility may use narrowly targeted implementation exceptions where required for reliable visually hidden content.

A site should normally be able to override StyleWire by loading its own stylesheet after `stylewire.css`, without specificity escalation.

## One-File Source

The distributed framework remains one readable CSS file.

StyleWire does not require:

- a build step
- a package manager
- a preprocessor
- generated utility classes
- JavaScript
- framework adapters
- bundled fonts or icons

The source file is the product, not an intermediate build artifact.

Documentation and the demonstration page may use separate files, but the framework itself remains directly readable and copyable.

## Stylesheet Order

`stylewire.css` is organized from broad foundations to narrower behavior:

1. variables and color themes
2. reset rules
3. document defaults
4. layout classes
5. typography
6. links and focus
7. navigation
8. content elements
9. tables
10. forms
11. buttons
12. components
13. responsive adjustments

New rules should be placed in the most relevant existing section. A new section should be added only when it represents a distinct framework concern.

## Variables and Local Customization

Public CSS variables hold shared framework values such as colors, spacing, widths, radii, and typography settings.

Variables provide the normal customization layer. Sites should prefer overriding a documented variable when changing a shared framework choice and use site-specific CSS for isolated behavior.

Component-specific variables may customize an individual `.stack`, `.cluster`, or `.columns` instance without creating additional classes.

See [CSS variables](variables.md) for the current variable reference and [Sizing and units](sizing.md) for unit policy.

## Public API Boundaries

The public API consists of documented classes, documented CSS variables, supported theme attributes, and the semantic element behavior users reasonably depend on.

Internal selector structure and one-off property values are implementation details unless documented otherwise.

StyleWire is pre-1.0 and does not promise API stability. Documented classes, variables, theme attributes, and semantic element behavior may change between minor releases. Changes should remain deliberate, narrowly scoped, and recorded in the changelog.

## Accessibility Baseline

Semantic HTML is preferred because native elements provide meaning and behavior that CSS should not recreate.

Framework additions should preserve:

- visible keyboard focus
- readable contrast
- native form behavior
- reasonable touch targets
- text resizing and browser font preferences
- assistive-technology access to visually hidden text

A visual component should not require replacing a native interactive element with a generic element.

See [Accessibility](accessibility.md) for the current framework baseline, author responsibilities, and basic testing guidance.

## Browser Approach

StyleWire targets modern browsers without transpilation or compatibility bundles.

For now, modern browsers means the current stable releases of Chrome, Edge, Firefox, and Safari. Internet Explorer and legacy browser-specific compatibility work are out of scope.

Progressive CSS features are acceptable when they simplify the source and fail safely where practical. A new feature should not create a serious usability failure in an otherwise supported browser merely to save a small amount of CSS.

## Evaluating New Features

Before adding an element style, class, variable, or component, ask:

1. Does it solve a common problem for semantic static sites?
2. Can ordinary HTML already express the intent adequately?
3. Does it require a framework class, or does it belong in site-specific CSS?
4. Can it remain understandable in one readable stylesheet?
5. Does it preserve accessibility and predictable overrides?
6. Is the long-term API cost justified by its usefulness?

When the answer is uncertain, leaving the feature out is usually safer. Sites can add local CSS more easily than the framework can remove an unnecessary public API later.

## Out of Scope

StyleWire is not intended to become:

- a comprehensive utility framework
- a JavaScript component library
- an application shell or routing system
- a generated design-system pipeline
- a collection of highly specialized page templates
- a replacement for site-specific styling

The goal is a dependable semantic foundation with a deliberately small extension layer.
