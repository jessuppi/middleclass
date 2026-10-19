# Localization

MiddleClass provides CSS styling, not a translation or localization system. Sites using the framework are responsible for their own languages, translated content, fonts, and language navigation.

## Language and Text Direction

Set the appropriate HTML language and direction for each page or section, such as `<html lang="ar" dir="rtl">`. MiddleClass uses logical alignment in some layouts, including `.push-end` and `.dropdown-start`, and adjusts single-select chevron placement for right-to-left text.

These features help with RTL layouts but do not amount to comprehensive testing or guaranteed compatibility for every script and writing direction.

## Site Responsibilities

- Provide accurate `lang` and `dir` attributes where needed.
- Choose fonts that support the site's languages, and test longer or shorter translated text for wrapping and overflow.
- Check navigation, dropdowns, forms, tables, and responsive layouts in each supported language.
- Handle translations, locale-specific formatting, alternate-language URLs, and related SEO metadata outside MiddleClass.

MiddleClass does not include translation files, language switching, routing, JavaScript localization tools, or bundled fonts. Keep these concerns in the website rather than the core `middleclass.css`.

See [Customization](customization.md) for font overrides, [Classes](classes.md) for direction-aware component behavior, and [Testing](testing.md) for manual checks.
