# 💩🌪️ Shitstorm - Sulphuris

The [shitstorm](https://github.com/stamat/shitstorm) base template with a [sulphuris](https://www.npmjs.com/package/sulphuris) CSS utility framework bolted on.

A small [Poops](https://github.com/stamat/poops/) template for static sites with JS + SCSS bundling and Markdown-based page generation, shipping [sulphuris](https://www.npmjs.com/package/sulphuris) for styling, [book-of-spells](https://www.npmjs.com/package/book-of-spells) for JS helpers, and a PostCSS pass that strips every unused rule out of the build.

## Out-of-the-box stack

| Layer         | Included                                                         |
| ------------- | ---------------------------------------------------------------- |
| Runtime       | Node.js + npm                                                    |
| Build tool    | `poops` (`npm run dev`, `npm run build`)                         |
| Scripts       | ES modules from `src/scripts/script.js`                          |
| Styles        | SCSS entry points in `src/styles/`                               |
| CSS framework | [`sulphuris`](https://www.npmjs.com/package/sulphuris)           |
| CSS pipeline  | PostCSS — [PurgeCSS](https://purgecss.com/) + comment stripping  |
| JS helpers    | [`book-of-spells`](https://www.npmjs.com/package/book-of-spells) |
| Markup        | Markdown content + layout templating in `src/markup/`            |
| Data          | YAML data files (example: `src/markup/_data/fonts.yaml`)         |
| Static assets | Copied from `src/static` to `dist`                               |
| Dev UX        | Local server on port `4040` + live reload                        |
| Lint          | ESLint (JS) + Stylelint (SCSS)                                   |
| Tests         | Jest (`npm test`)                                                |
| CI            | GitHub Actions — lint + test on push/PR, deploy on `main`        |
| Output        | Built site in `dist/` with minified assets + source maps         |

## Project structure

```text
src/
  markup/     # pages, layouts, data
  scripts/    # JavaScript entry points
  styles/     # SCSS entry points and config
  static/     # copied as-is to dist
.tmp/         # intermediate SCSS output, PostCSS input
dist/         # generated output
poops.json    # build + serve config
```

## Quick start

Scaffold a project from this template with [create-poops](https://github.com/stamat/create-poops):

```bash
npm create poops@latest my-app sulphuris
```

Omit the template name to pick from a prompt (`base`, `sulphuris`, `hat`), or omit the target directory to scaffold into the current one. Needs `git` on your `PATH`; the clone's history is dropped so you start clean.

Then:

```bash
cd my-app
npm install
npm run dev
```

Build for production:

```bash
npm run build
```

## CSS pipeline

`src/styles/site.scss` compiles to `.tmp/site.css`, then PostCSS purges it and writes `dist/styles/site.css` and `site.min.css`. Sulphuris ships ~133KB of utilities; the built site keeps ~8KB of them.

PurgeCSS scans `dist/**/*.html` and `dist/scripts/*.js`, so a class only survives if it appears in the built output. Classes you attach at runtime from JS won't be found — add them to `safelist` in the plugin options in [`poops.json`](poops.json).

The intermediate lives outside `dist/` on purpose: PostCSS re-runs on every markup change, and purging an already-purged file would permanently drop classes added later. One side effect — `site.css` has no source map, since the PostCSS pipeline doesn't emit one.

## Checks

```bash
npm run lint   # ESLint (JS) + Stylelint (SCSS)
npm test       # Jest — builds and asserts dist/ output
```

CI runs both on every push and pull request ([`.github/workflows/ci.yml`](.github/workflows/ci.yml)); pushes to `main` also deploy to GitHub Pages ([`.github/workflows/pages.yml`](.github/workflows/pages.yml)).
