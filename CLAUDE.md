# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

The documentation site for **Gerillass**, an open-source Sass mixin/function library
(library source lives in a separate repo: `selfishprimate/gerillass`). Built with the
**Hugo** static site generator and deployed to Netlify at `https://docs.gerillass.com/`.

The site is a customized derivative of the *Hugo Book* theme, but there is **no `themes/`
directory** — the theme was vendored directly into the repo root (`layouts/`, `assets/`,
`i18n/`, `static/`). Every template is editable in place.

## Commands

```bash
npm install          # installs the only dependency: gerillass (used to style this site)
hugo server -D       # local dev server at http://localhost:1313 with live reload
hugo --gc --minify   # production build into ./public (same command Netlify runs)
```

There is no test suite and no linter (`npm test` is the npm placeholder stub and will fail).

## Build requirements (Dart Sass)

`layouts/partials/docs/html-head.html` compiles the stylesheet with:

```
css.Sass (dict "transpiler" "dartsass" "includePaths" (slice "node_modules"))
```

The `dartsass` transpiler needs the **`sass` binary on `PATH`** — Hugo does not bundle it.
(The extended edition only matters for the default `libsass` transpiler, which this site no
longer uses, so any Hugo edition works as long as Dart Sass is installed.) Locally:
`brew install sass/sass/sass`.

Netlify's build image does not ship Dart Sass either, so every build command in
`netlify.toml` downloads it and prepends it to `PATH` before calling `hugo`. Versions are
pinned once in `[build.environment]` (`HUGO_VERSION`, `DART_SASS_VERSION`) and shared by all
contexts — bump them there, not per-context.

`includePaths: node_modules` is what lets the partials write
`@use "gerillass/scss/gerillass" as *` without a `./node_modules/` prefix. Don't
reintroduce the prefixed form.
## Sass architecture

- The stylesheet is on the Sass **module system** throughout. There is not a single
  `@import` left, and the build emits **zero** deprecation warnings.
- Every partial declares its own dependencies at the top with `@use`. Nothing is global any
  more, so a partial that needs something must ask for it: `"variables" as *` for the site's
  variables, `"icons" as *` for the icon font names, `"utils" as *` for the local `spin`
  mixin, `"gerillass/scss/gerillass" as *` for the library, and `sass:math` / `sass:color`
  for the built-ins. Sass will name the file and line if you forget one.
- `assets/scss/styles.scss` only loads the partials, in the order their CSS should appear in
  the output. A new `_foo.scss` does nothing until it is registered there. (`_numbered.scss`
  is not registered and is therefore dead.)
- The site is on **Gerillass 2.0.0**, which is Dart-Sass-only and built on the Sass module
  system. Version 2.0.0 dropped the `__` prefix from every utility function, so the partials
  call `remify()`, not `__remify()`. Get this wrong and it fails **silently**: Sass passes an
  unknown function through as literal CSS instead of raising an error, so the build still
  succeeds and the declaration is simply invalid. `grep -rn '__remify' assets/` should stay
  empty. BEM class names like `&__link` are unrelated and must not be touched.
- If you ever see a deprecation warning from a build, it is new. The count was 142 on
  Gerillass 1.3.1 with `@import`, and is 0 now.

## Content model

Each documented mixin/function is a **leaf bundle**: `content/docs/<mixin-name>/index.md`,
with page-local assets alongside it (`images/`, occasionally `css/`, sprite PNGs, etc.).
`content/_index.md` is the "Getting Started" / installation page.

Frontmatter fields that actually drive templates:

| Field | Effect |
|---|---|
| `title` | menu label and page title fallback |
| `page_title` | overrides `<title>` (SEO) |
| `page_description` | overrides `<meta name="description">` |
| `page_keywords` | overrides `<meta name="keywords">` |
| `css` | injects an extra stylesheet, path relative to the bundle (see `docs/loadify`) |

No page sets `weight`, so the sidebar is generated from the file tree
(`BookSection = "docs"` in `config.toml`) and ordered alphabetically. Use
`hugo new docs/<name>/index.md -k docs` for the docs archetype.

## Shortcodes — the docs authoring API

Content pages are written almost entirely with shortcodes in `layouts/shortcodes/`:

- `{{< mixin type="Mixin" name="<name>" >}}…{{< /mixin >}}` — page header block. The `name`
  is used to build a GitHub source link to
  `gerillass/scss/library/_<name>.scss`, so it **must match the library filename**.
- `{{< function type="Function" name="<name>" >}}` — same idea, but links into
  `gerillass/scss/utilities/_<name>.scss`.
- `{{< arguments/table footnote="…" >}}` wrapping one `{{< arguments/row name= type= description= >}}`
  per argument — the arguments reference table.
- `{{< highlightwrap class="terminal|example" >}}` wrapping Hugo's built-in
  `{{< highlight scss >}}` / `{{< highlight css >}}` blocks — the standard
  "SCSS input + CSS output" pairing used throughout.
- `{{< hint info >}}` — callout box.
- `{{< sandbox class="small|medium|large|xlarge" >}}` — its inner text is injected raw as an
  inline `style` attribute on an empty div, giving a live visual preview of the CSS output.

When adding a new mixin page, copy the structure of an existing one (e.g.
`content/docs/adaptive/index.md`): H1 → `mixin` block → explanation → `## Arguments` table →
`## Examples` with paired SCSS/CSS highlight blocks.

## Other things worth knowing

- `resources/_gen/` (Hugo's asset cache) **is committed to git**, so SCSS changes produce
  churn there. The files are regenerable; deleting stale ones is safe.
- `public/` and `node_modules/` are gitignored. `cleanDestinationDir = true` means Hugo
  wipes unused files from `public/` on each build.
- Search is FlexSearch, built client-side: `assets/search.js` + `assets/search-data.js`
  (both are Go templates run through `resources.ExecuteAsTemplate`, so they can use Hugo
  template syntax). `static/flexsearch.min.js` is the vendored library.
- Icons come from the remote Ionicons script tag in `layouts/_default/baseof.html` plus a
  self-hosted icon font in `static/icons/gerillass/`.
- `i18n/` carries translations for six languages, but only English is configured; the
  language switcher partial is inert while the site is monolingual.
- Google Analytics runs off a **hardcoded** gtag snippet in `layouts/_default/baseof.html`
  (`UA-171697118-2`). `html-head.html` also calls `_internal/google_analytics.html`, but that
  renders nothing because no analytics ID is set in `config.toml`.
