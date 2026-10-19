# Attribution

MiddleClass separates third-party attribution for the distributable CSS framework from attribution for assets used only by this repository's demo website.

## Core Stylesheet

The project's original CSS is licensed under its [MIT License](../license) and distributed as `middleclass.css`. That stylesheet also embeds the Font Awesome Free 7.3.1 `chevron-down` icon for native single-select controls and dropdown triggers. The embedded third-party icon remains subject to its own CC BY 4.0 license; the project's MIT license does not replace that requirement.

Font Awesome SVG icons are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The chevron's SVG packaging and view box were adjusted for CSS use. The stylesheet retains an attribution comment identifying Font Awesome, its copyright, the license, the source, and the modification, so sites copying the CSS retain that information.

The repository also maintains [`notices.md`](../notices.md) as its central record of third-party credits and license texts relevant to the core CSS, including the bundled Font Awesome icon. This is an **additional documentation and transparency measure**, not a separately prescribed `notices.md` file requirement. It does not replace the attribution retained in the standalone stylesheet.

## Demo Website

The GitHub Pages demo (`index.html`) separately uses two Font Awesome Free 7.3.1 SVG assets:

- [`assets/icons/download.svg`](../assets/icons/download.svg) for the Download button
- [`assets/icons/github.svg`](../assets/icons/github.svg) for the GitHub repository button

These icons are referenced through CSS masks in the demo and are **not part of `middleclass.css`**. Both original SVG files contain embedded Font Awesome attribution, copyright, and license comments. Their accompanying button text provides the accessible name, while the decorative icons are hidden from assistive technology.

Font Awesome says its Free files normally include sufficient attribution in their embedded comments. Attribution is still required; a separate visible credit or extra notices file is not generally needed merely because the unmodified SVGs are used in the demo. The GitHub brand icon should only represent GitHub and does not imply endorsement.

## Maintenance

- Keep upstream attribution and license references with third-party assets. Do not strip their comments without preserving sufficient attribution elsewhere.
- Identify modifications to CC BY 4.0 icons and retain appropriate credit when repackaging them.
- Keep `notices.md` focused on third-party material distributed in the core stylesheet. Document demo-only icon use here instead.
- Review this distinction when adding, replacing, modifying, or moving icons between the demo and framework.

For licensing details, see [Font Awesome Free's official license explanation](https://github.com/FortAwesome/Font-Awesome#license) and [CC BY 4.0 attribution requirements](https://creativecommons.org/licenses/by/4.0/legalcode.en#s3).
