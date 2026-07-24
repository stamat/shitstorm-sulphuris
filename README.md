# 💩🌪️ Shitstorm

A small [Poops](https://github.com/stamat/poops/) template for static sites with JS + SCSS bundling and Markdown-based page generation.

## Out-of-the-box stack

| Layer | Included |
| --- | --- |
| Runtime | Node.js + npm |
| Build tool | `poops` (`npm run dev`, `npm run build`) |
| Scripts | ES modules from `src/scripts/script.js` |
| Styles | SCSS entry points in `src/styles/` |
| CSS framework | [`sulphuris`](https://www.npmjs.com/package/sulphuris) |
| JS helpers | [`book-of-spells`](https://www.npmjs.com/package/book-of-spells) |
| Markup | Markdown content + layout templating in `src/markup/` |
| Data | YAML data files (example: `src/markup/_data/fonts.yaml`) |
| Static assets | Copied from `src/static` to `dist` |
| Dev UX | Local server on port `4040` + live reload |
| Lint | ESLint (JS) + Stylelint (SCSS) |
| Tests | Jest (`npm test`) |
| CI | GitHub Actions — lint + test on push/PR, deploy on `main` |
| Output | Built site in `dist/` with minified assets + source maps |

## Project structure

```text
src/
  markup/     # pages, layouts, data
  scripts/    # JavaScript entry points
  styles/     # SCSS entry points and config
  static/     # copied as-is to dist
dist/         # generated output
poops.json    # build + serve config
```

## Quick start

```bash
npm install
npm run dev
```

Build for production:

```bash
npm run build
```

## Checks

```bash
npm run lint   # ESLint (JS) + Stylelint (SCSS)
npm test       # Jest — builds and asserts dist/ output
```

CI runs both on every push and pull request ([`.github/workflows/ci.yml`](.github/workflows/ci.yml)); pushes to `main` also deploy to GitHub Pages ([`.github/workflows/pages.yml`](.github/workflows/pages.yml)).
