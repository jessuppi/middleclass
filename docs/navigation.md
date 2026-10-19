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

Unclassed `<details>` elements are ordinary in-flow disclosures. For an overlaid navigation panel, MiddleClass already supports `<details class="dropdown">` with a direct `<summary>` followed by a direct `<ul>` of links. Its CSS positions the panel without shifting surrounding content and allows pointer clicks outside the open panel to dismiss it without JavaScript.

The `.dropdown-start` and `.dropup` modifiers adjust panel alignment and opening direction; they do not automatically detect viewport space. See [Classes](classes.md) for supported markup and [Accessibility](accessibility.md) for keyboard and navigation guidance.

For behavior beyond the built-in disclosure and dropdown, such as specialized Escape-key handling or coordinated state across several menus, keep any scripting site-specific and test it with keyboard and assistive technology. Do not add application-style `menu` or `menuitem` roles to ordinary website navigation. Standard navigation should remain a normal `nav` containing ordinary links.

## When Not to Use It

For a small number of important links, plain navigation links are usually better. Use disclosure navigation when grouping related destinations improves clarity.

MiddleClass intentionally avoids bundling navigation JavaScript so sites can choose the appropriate level of interaction for their needs.
