# Spacing

MiddleClass uses a small spacing scale and a bottom-margin-first vertical rhythm. The goal is to keep ordinary document flow predictable while leaving structural and layout decisions explicit.

## Core Policy

Normal content elements create space after themselves, not before themselves.

- headings use a bottom margin and no default top margin
- ordinary block content uses a bottom margin and no default top margin
- the preceding element normally provides the space above the next element
- structural elements do not receive generic vertical margins
- layout classes control spacing among their children but remain externally marginless

This avoids doubled gaps when one element follows another and keeps spacing ownership easy to understand.

## Default Flow Spacing

MiddleClass currently uses these main relationships:

| Relationship | Default |
| --- | ---: |
| heading to following content | `--mc-space-4` (`1rem`) |
| ordinary block to following content | `--mc-space-5` (`1.5rem`) |
| adjacent list items | `--mc-space-2` (`0.5rem`) |
| definition term after a definition | `--mc-space-3` (`0.75rem`) |
| caption above a table | `--mc-space-3` (`0.75rem`) |
| figure content to its caption | `--mc-space-2` (`0.5rem`) |
| open disclosure summary to its content | `--mc-space-4` (`1rem`) |

`h1` through `h6` use no default top margin and use `--mc-space-4` below.

Paragraphs, lists, definition lists, blockquotes, code blocks, tables, figures, forms, and disclosures use no default top margin and use `--mc-space-5` below.

Lists nested directly inside a list item do not keep that full bottom margin. The normal adjacent-item gap controls the space before the next parent-level item instead.

## Structural Elements

Structural elements such as `div`, `section`, `article`, `header`, `main`, `footer`, `nav`, `aside`, and `address` do not receive generic vertical margins.

These elements describe document structure and may be nested in many different ways. Giving them automatic margins would make spacing depend on nesting rather than the intended relationship between visible content.

Structural elements may still receive intentional padding, borders, widths, or layout behavior. The no-margin policy applies only to generic external vertical spacing.

## Layout Classes

Layout classes control internal arrangement and remain externally marginless by default. Their parent provides any spacing before or after them.

- `.stack` arranges direct children vertically and uses `gap` as the single spacing source between those children
- `.cluster` controls wrapping horizontal space among related items
- `.columns` controls the row and column gaps among its grid items
- `.container` and `.reading-width` control width rather than vertical spacing
- `.push-end` controls inline alignment rather than vertical spacing

A layout class should not add an outside bottom margin merely because it contains visually substantial content. Place it inside a parent layout, such as `.stack`, when consistent spacing between larger groups is needed.

## Padded Components

At the top and bottom edges of a padded component, the component's padding should be the only spacing source.

The first child has no top margin, and the last child's bottom margin is removed. This prevents child margins from adding extra space on top of the component's own padding.

Child padding is not removed or changed. Padding that belongs to a child remains part of that child's own design.

This policy applies to contained surfaces such as cards, notices, blockquotes, fieldsets, and disclosures. Some first-child margins are already zero because MiddleClass does not give ordinary elements default top margins; explicit edge normalization also protects components from compatible local overrides.

## Contextual Top Margins

Bottom-margin-first does not mean that every top margin is forbidden. Small top margins are appropriate when they describe a relationship inside one element or content group.

Examples include:

- space between adjacent list items
- space before a new definition term
- space before a figure caption
- space between an open disclosure summary and its content

These are internal relationships, not generic outside spacing for structural containers.

## Horizontal Rules

`hr` is an intentional exception. It represents a thematic break and currently uses `--mc-space-7` above and below.

This symmetric spacing is deliberate because the rule separates two content groups rather than belonging more strongly to either one. It should be reviewed independently from ordinary flow margins.

## Avoiding Double Spacing

Use one clear spacing source for each relationship:

- ordinary document flow uses the preceding element's bottom margin
- a gap-based layout uses its `gap` between direct children
- a padded component uses its own padding at its outer inner edges
- a parent layout provides space around structural or layout groups

Do not add a generic structural margin merely to compensate for missing layout structure. Do not combine a parent `gap` with direct-child margins when the gap is intended to be the sole spacing mechanism.

## Review Process

Spacing changes should be tested in the live demo before becoming framework defaults. Review headings after different content elements, padded component edges, gap-based layouts, narrow screens, and both color themes.

The demo includes a dedicated vertical-rhythm area for this purpose. Changes should remain staged so one relationship can be judged without unintentionally changing the entire document rhythm.
