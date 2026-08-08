# AGENTS.md

## Repository purpose

This repository contains the Hexo source for [lichye.github.io](https://lichye.github.io). Treat it as the source of truth for the website; generated output belongs in the separate `lichye/lichye.github.io` repository.

## Project map

- `_config.yml`: site-wide Hexo settings and deployment target.
- `source/`: page and post content that Hexo renders.
- `themes/Academia/`: the vendored, customized Academia theme.
- `themes/Academia/_config.yml`: theme-specific content and presentation settings.
- `themes/Academia/layout/`: Pug templates for page structure.
- `themes/Academia/source/css/`: Stylus stylesheets.
- `themes/Academia/source/js/`: browser-side JavaScript.
- `themes/Academia/source/img/` and `themes/Academia/source/attaches/`: images, the CV, papers, and slides published by the theme.

## Working rules

- Make content changes in `source/` and presentation changes in `themes/Academia/`.
- Keep the Academia theme vendored as normal files. Do not turn it into a Git submodule or restore a nested `.git` directory.
- Preserve existing URLs and filenames unless a requested change explicitly requires a migration.
- Do not remove the Google verification file, `robots.txt`, or `sitemap.xml` without an explicit reason.
- Do not edit or commit generated and local-only paths: `node_modules/`, `public/`, `db.json`, `.deploy_git/`, or files ending in `:Zone.Identifier`.
- Do not run `npm run deploy` or push generated files to `lichye/lichye.github.io` unless the user explicitly asks to publish the website.
- Avoid unrelated visual or content changes. Keep the site responsive and check both narrow and wide layouts when changing templates or CSS.

## Setup and validation

Install dependencies from the lockfile:

```bash
npm ci
```

Before handing off a website change, run a clean production build:

```bash
npm run clean
npm run build
```

For interactive review, run:

```bash
npm run server
```

The production build must complete without errors. Confirm that `public/index.html`, `public/robots.txt`, and `public/sitemap.xml` exist, and inspect the affected generated page or asset rather than relying only on the build exit code.

## Git expectations

- Keep commits focused and describe the user-visible change.
- Review `git status` before committing so ignored build output or unrelated files are not included.
- Source changes go to this repository; deployment output goes only to the separate Pages repository.
