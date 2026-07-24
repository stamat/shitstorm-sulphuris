---
layout: default
---

# {{ site.title }}

{{ site.description }}

Built with [Poops](https://github.com/stamat/poops/) - super fast and easy bundler and static site generator.

<a class="btn mb-32" href="https://github.com/stamat/shitstorm-sulphuris">
  <svg class="mr-8" width="20" height="20" viewBox="0 0 16 16" fill="currentColor" aria-hidden="true"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8Z"/></svg>
  View on GitHub
</a>

## What's in the box

<div class="grid grid-gutter mb-32">
  <div class="col-12 col-lg-4 mb-16">
    <div class="border border-primary rounded-8 p-24 h-100p">
      <div class="text-uppercase text-bold text-primary">Styles</div>
      <p class="mt-8 mb-0"><a href="https://github.com/stamat/sulphuris">sulphuris</a> - an adaptable CSS utility library, configured in <code>src/styles/_config.scss</code>.</p>
    </div>
  </div>
  <div class="col-12 col-lg-4 mb-16">
    <div class="border border-primary rounded-8 p-24 h-100p">
      <div class="text-uppercase text-bold text-primary">Scripts</div>
      <p class="mt-8 mb-0"><a href="https://github.com/stamat/book-of-spells">book-of-spells</a> - a tiny helper library, imported in <code>src/scripts/script.js</code>.</p>
    </div>
  </div>
  <div class="col-12 col-lg-4 mb-16">
    <div class="border border-primary rounded-8 p-24 h-100p">
      <div class="text-uppercase text-bold text-primary">Markup</div>
      <p class="mt-8 mb-0">Markdown pages and layouts in <code>src/markup/</code>, rendered by Poops.</p>
    </div>
  </div>
</div>

## Getting started

Scaffold your own copy with [create-poops](https://github.com/stamat/create-poops):

```bash
npm create poops@latest my-app sulphuris
cd my-app
npm install
npm run dev
```

`npm run dev` serves the site on port `4040` with live reload. `npm run build` writes the production build to `dist/`.

## Styling

Override the [sulphuris config](https://github.com/stamat/sulphuris/blob/main/src/core/_config.scss) variables in `src/styles/_config.scss` - colors, breakpoints, container width, fonts - then use the generated utility classes in your markup. The row above is one `.grid.grid-gutter` of `.col-12.col-lg-4` columns.

```scss
$colors: (
  black: #000,
  white: #fff,
  primary: #824f2d,
  brownish: #dcc8ac,
);
```

<div class="grid grid-gutter mb-32">
  <div class="col-12 col-lg-6 mb-16">
    <div class="bg-primary text-white rounded-8 p-16 text-center">.bg-primary .text-white</div>
  </div>
  <div class="col-12 col-lg-6 mb-16">
    <div class="bg-black text-white rounded-8 p-16 text-center">.bg-black .text-white</div>
  </div>
</div>

## One catch: PurgeCSS

The build runs the compiled CSS through [PurgeCSS](https://purgecss.com/), scanning `dist/**/*.html` and `dist/scripts/*.js`. Only classes that appear in the built output survive - sulphuris drops from ~133KB to ~8KB.

Classes you add from JavaScript at runtime won't be found by the scan. Add those to `safelist` in the plugin options in `poops.json`.
