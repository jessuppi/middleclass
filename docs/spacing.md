# Spacing

MiddleClass uses a small spacing scale and a bottom-margin-first vertical rhythm. The goal is to keep ordinary document flow predictable while giving headings enough separation to signal a new section or subsection.

## Core Policy

Normal content elements create space after themselves rather than before themselves. Headings that commonly introduce a new section are the intentional exception.

- `h1` uses a bottom margin and no default top margin
- `h2` through `h6` use hierarchical top margins plus a consistent bottom margin
- ordinary block content uses a bottom margin and no default top margin
- structural elements do not receive generic vertical margins
- layout classes control spacing among their children but remain externally marginless

This keeps ordinary flow simple while making section and subsection boundaries visually clearer without requiring separator elements or project-specific spacing rules.

## Default Flow Spacing

MiddleClass currently uses these main relationships:

| Relationship | Default |
| --- | ---: |
| `h2` top separation | `--mc-space-7` (`3rem`) |
| `h3` through `h6` top separation | `--mc-space-6` (`2rem`) |
| heading to following content | `--mc-space-4` (`1rem`) |
| ordinary block to following content | `--mc-space-5` (`1.5rem`) |
| adjacent list items | `--mc-space-2` (`0.5rem`) |
| definition term after a definition | `--mc-space-3` (`0.75rem`) |
| caption above a table | `--mc-space-3` (`0.75rem`) |
| figure content to its caption | `--mc-space-2` (`0.5rem`) |
| open disclosure summary to its content | `--mc-space-4` (`1rem`) |

`h1` uses no default top margin and uses `--mc-space-4` below. `h2` uses `--mc-space-7` above, while `h3` through `h6` use `--mc-space-6` above. All heading levels use `--mc-space-4` below.

Paragraphs, lists, definition lists, blockquotes, code blocks, tables, figures, forms, disclosures, and notices use no default top margin and use `--mc-space-5` below.

In ordinary block flow, adjacent vertical margins collapse. A paragraph followed by an `h2`, for example, resolves to the larger `3rem` heading margin rather than adding the paragraph's `1.5rem` bottom margin to it.

A list nested as the final child of a list item does not keep that full bottom margin. The normal adjacent-item gap controls the space before the next parent-level item instead, while a nested list followed by more content keeps its ordinary bottom spacing.

## Structural Elements

Structural elements such as `div`, `section`, `article`, `header`, `main`, `footer`, `nav`, `aside`, and `address` do not receive generic vertical margins.

These elements describe document structure and may be nested in many different ways. Giving them automatic margins would make spacing depend on nesting rather than the intended relationship between visible content.

Structural elements may still receive intentional padding, borders, widths, or layout behavior. The no-margin policy applies only to generic external vertical spacing. A structural element using the `.notice` component is an explicit exception and receives the standard ordinary block bottom spacing.

## Layout Classes

Layout classes control internal arrangement and remain externally marginless by default. Their parent provides any spacing before or after them.

- `.stack` arranges direct children vertically and uses `gap` as the single spacing source between those children
- `.cluster` controls wrapping horizontal space among related items
- `.columns` controls the row and column gaps among its grid items
- `.container` and `.reading-width` control width rather than vertical spacing
- `.push-end` controls inline alignment rather than vertical spacing

Direct children of `.stack`, including headings and notices, have their block margins normalized to zero so the stack's `gap` remains the sole spacing source. Heading top margins therefore affect ordinary document flow but do not compound a gap-based layout.

A layout class should not add an outside bottom margin merely because it contains visually substantial content. Place it inside a parent layout, such as `.stack`, when consistent spacing between larger groups is needed.

## Padded Components

At the top and bottom edges of a padded component, the component's padding should be the only spacing source.

The first child has no top margin, and the last child's bottom margin is removed. This prevents child margins from adding extra space on top of the component's own padding.

Child padding is not removed or changed. Padding that belongs to a child remains part of that child's own design.

This policy applies to contained surfaces such as cards, notices, blockquotes, fieldsets, and disclosures. Explicit edge normalization prevents a heading's top margin from adding to a component's top padding when that heading is the first child. A notice's own external bottom margin is separate from this internal edge normalization.

## Contextual Top Margins

Bottom-margin-first does not mean that every top margin is forbidden. Top margins are appropriate when they communicate a meaningful relationship that cannot be expressed as ordinary trailing flow spacing.

The primary example is heading hierarchy:

- `h2` receives the strongest top separation because it commonly begins a major section
- `h3` through `h6` receive a smaller but clear top separation for subsections and lower-level structure

Other contextual examples include:

- space between adjacent list items
- space before a new definition term
- space before a figure caption
- space between an open disclosure summary and its content

These are intentional relationships, not generic outside spacing for structural containers.

## Horizontal Rules

`hr` is an intentional exception. In ordinary flow it uses `--mc-space-7` above and below.

This symmetric spacing is deliberate because the rule separates two content groups rather than belonging more strongly to either one. As with other direct children of `.stack`, its margins are normalized when a stack's `gap` is intended to own the spacing.

## Avoiding Double Spacing

Use one clear spacing source for each relationship:

- ordinary document flow uses block margins, with heading top margins providing stronger section separation
- adjacent vertical margins collapse rather than being added together in ordinary block flow
- a gap-based layout uses its `gap` between direct children and normalizes those children's block margins
- a padded component uses its own padding at its outer inner edges
- a parent layout provides space around structural or layout groups

Do not add a generic structural margin merely to compensate for missing layout structure. Do not combine a parent `gap` with direct-child margins when the gap is intended to be the sole spacing mechanism.

## Review Process

Spacing changes should be tested in the live demo before becoming framework defaults. Review headings after different content elements, padded component edges, gap-based layouts, narrow screens, and both color themes.

The demo includes a dedicated vertical-rhythm area for this purpose. Changes should remain staged so one relationship can be judged without unintentionally changing the entire document rhythm.
