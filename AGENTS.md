# Repository Instructions

This repository is a personal GitHub Pages site built with Jekyll. Keep changes focused on the site content and presentation, not the generated output.

## Where to work

- Homepage content lives in [index.md](index.md) front matter.
- Shared page structure lives in [_layouts/default.html](_layouts/default.html).
- Site styling lives in [assets/css/style.scss](assets/css/style.scss).
- Local setup and run steps are documented in [README.md](README.md).

## Editing conventions

- Treat the homepage as front matter driven: update the variables in `index.md` and the Liquid references in `_layouts/default.html` together.
- Keep the dark Midnight-inspired visual direction in `style.scss`; extend the existing CSS variables and patterns instead of introducing a new theme.
- Preserve accessibility features such as the skip link, semantic headings, and descriptive link text.
- Do not edit files under `_site/`; they are generated build artifacts.

## Verification

- Use `bundle install` and `bundle exec jekyll serve` to check the site after content, layout, or styling changes.
- If a change affects navigation or section structure, verify the matching anchors and layout references still line up.