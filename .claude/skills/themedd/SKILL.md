---
name: themedd
description: Repository-specific development guidance for Themedd WordPress theme, including Easy Digital Downloads integration, templates, hooks, theme compatibility, PHP, JS, CSS, accessibility and backward compatibility.
---

# Themedd Theme

## Architecture
- Theme bootstrap: `functions.php`.
- Shared theme code: `includes/`.
- Templates include standard theme files plus EDD-specific templates under `edd_templates/`.
- Page templates live under `page-templates/`; reusable pieces under `template-parts/`.
- Frontend assets live under `assets/`.
- Grunt handles LESS/JS and asset processing.
- The theme includes compatibility handling for older WordPress versions.

## Theme-specific rules
- Do not put user customizations into `functions.php`; preserve the documented child-theme/custom-plugin approach.
- Preserve Easy Digital Downloads integration and existing template hooks.
- Before changing a template, check whether the behavior is inherited by archive, single, taxonomy, EDD and page-template contexts.
- Preserve theme support, Customizer behavior, menus, widgets, sidebars and updater behavior.
- Avoid breaking child themes by renaming/removing template hooks, classes or filters without a compatibility layer.

## WordPress standards
- Follow current WordPress PHP, JS, CSS and HTML Coding Standards.
- Follow WordPress theme internationalization and accessibility guidance.
- New/changed UI should target WCAG 2.2 AA.
- Escape template output late and sanitize/validate incoming values.
- Use nonces plus capability checks for privileged admin actions.
- Preserve the `themedd` text domain.
- Avoid unnecessary global state and direct database access.

## PHP compatibility
- Existing theme code supports older WordPress versions; do not assume modern WordPress-only APIs without a compatibility check.
- Determine the minimum WordPress/PHP version before introducing new syntax or APIs.
- New PHP should remain compatible with the declared minimum and current PHP versions supported by WordPress.
- Use PHPCompatibilityWP/PHPCS when PHP tooling is available.
- Prefer WordPress compatibility helpers and version checks over breaking old installations.

## JavaScript/CSS
- Keep the existing Grunt pipeline and do not hand-edit generated/minified assets when source files exist.
- Preserve responsive layouts, RTL behavior and keyboard accessibility.
- Avoid broad selectors that can break EDD or child-theme markup.
- Use WordPress JS conventions and safe event handling.

## Verification
Test at minimum: front page, archives, single post/download, taxonomy, search, comments, widgets/sidebars, page templates, EDD purchase/download flows, Customizer changes and child-theme compatibility.
