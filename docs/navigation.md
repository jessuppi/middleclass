# Navigation

MiddleClass keeps interactive behavior lightweight. For navigation that needs expandable sections, prefer native HTML disclosure elements before adding JavaScript.

## Details Navigation

The native `details` and `summary` elements are a useful baseline for simple navigation groups:

```html
<details>
	<summary>Websites</summary>
	<ul>
		<li><a href="/static-websites/">Static Websites</a></li>
		<li><a href="/business-websites/">Business Websites</a></li>
	</ul>
</details>
```

This provides:

- keyboard-operable controls
- ordinary links that work without scripting
- progressive enhancement opportunities
- minimal CSS requirements

## Dropdown Enhancement

`details` is a disclosure component, not a complete application-style mega menu. If a site needs richer desktop dropdown behavior, add a small site-specific enhancement rather than adding framework JavaScript.

Good enhancements may include:

- improved open and close behavior
- closing when clicking outside
- Escape key handling
- synchronized `aria-expanded` states

Avoid replacing normal website navigation with application-style `menu` roles. Standard navigation should remain a normal `nav` containing ordinary links.

## When Not to Use It

For a small number of important links, plain navigation links are usually better. Use disclosure navigation when grouping related destinations improves clarity.

MiddleClass intentionally avoids bundling navigation JavaScript so sites can choose the appropriate level of interaction for their needs.
