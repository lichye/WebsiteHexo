# WebsiteHexo

Source code for [lichye.github.io](https://lichye.github.io), built with [Hexo](https://hexo.io/) and a customized, vendored Academia theme.

## Requirements

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/) `>= 20.19.0`
- npm, which is included with Node.js

The repository currently locks Hexo `8.1.1`. A clean build has been verified with Node.js `24.11.0` and npm `10.8.2`.

Check the installed tools:

```bash
git --version
node --version
npm --version
```

If Node.js is missing, install a current LTS release from the Node.js website or with a version manager such as `nvm`. With `nvm` already installed, for example:

```bash
nvm install 24
nvm use 24
```

## Clone the source

Using SSH:

```bash
git clone git@github.com:lichye/WebsiteHexo.git
cd WebsiteHexo
```

Or using HTTPS:

```bash
git clone https://github.com/lichye/WebsiteHexo.git
cd WebsiteHexo
```

## Install Hexo and the project dependencies

A global Hexo installation is not required. The recommended command installs the project-local Hexo version and every plugin recorded in `package-lock.json`:

```bash
npm ci
```

Verify the local installation:

```bash
npx hexo version
```

Use `npm ci` for a fresh clone and for reproducible builds. Use `npm install` only when intentionally adding or updating a dependency, because it can change `package-lock.json`.

If a global Hexo command is specifically desired, it is optional:

```bash
npm install --global hexo-cli
hexo version
```

The npm scripts in this repository use the local Hexo binary, so the global CLI is never needed for normal development.

## Included dependencies

All direct dependencies are declared in `package.json`, and exact transitive versions are locked in `package-lock.json`.

| Package group | Packages | Purpose |
| --- | --- | --- |
| Core | `hexo` | Generates the static website. |
| Local preview | `hexo-server` | Serves the generated site during development. |
| Deployment | `hexo-deployer-git` | Publishes generated output to the Pages repository. |
| Generators | `hexo-generator-archive`, `hexo-generator-category`, `hexo-generator-index`, `hexo-generator-tag` | Generate index, archive, category, and tag pages. |
| Renderers | `hexo-renderer-ejs`, `hexo-renderer-marked`, `hexo-renderer-pug`, `hexo-renderer-stylus` | Render templates, Markdown, Pug, and Stylus files. |
| Packaged fallback theme | `hexo-theme-landscape` | Provides Hexo's packaged fallback theme; the live site uses the customized `themes/Academia` theme. |

Do not install these packages one by one. `npm ci` installs the complete compatible set from the lockfile.

## Preview locally

Start the development server:

```bash
npm run server
```

Open [http://localhost:4000](http://localhost:4000). Stop the server with `Ctrl+C`.

## Build the production site

Run a clean build:

```bash
npm run clean
npm run build
```

The generated website is written to `public/`. Confirm that at least these files exist:

```text
public/index.html
public/robots.txt
public/sitemap.xml
```

`public/`, `node_modules/`, `db.json`, and `.deploy_git/` are generated or local-only and must not be committed.

## Modify the website

- Edit pages and posts in `source/`.
- Edit site-wide settings in `_config.yml`.
- Edit theme settings in `themes/Academia/_config.yml`.
- Edit Pug templates in `themes/Academia/layout/`.
- Edit styles and browser JavaScript in `themes/Academia/source/css/` and `themes/Academia/source/js/`.
- Store published images, the CV, papers, and slides under `themes/Academia/source/`.

The customized Academia theme is committed as normal files so the complete site can be reproduced from this repository. Do not convert it into a Git submodule.

See [`AGENTS.md`](AGENTS.md) for repository-specific editing and validation rules.

## Deploy

The source repository and the published Pages repository are separate. `_config.yml` currently defines the deployment target for `lichye.github.io`.

Only deploy after reviewing the generated site and confirming GitHub authentication:

```bash
npm run clean
npm run build
npm run deploy
```

`npm run deploy` writes generated files to the Pages repository and changes the live website. Do not run it for ordinary source-only edits.

## Common commands

| Command | Action |
| --- | --- |
| `npm ci` | Install the exact dependency set from the lockfile. |
| `npx hexo version` | Show the local Hexo and environment versions. |
| `npm run server` | Start the local preview server. |
| `npm run clean` | Remove generated output and the Hexo database. |
| `npm run build` | Generate the production site in `public/`. |
| `npm run deploy` | Publish the generated site; use only when explicitly intended. |
