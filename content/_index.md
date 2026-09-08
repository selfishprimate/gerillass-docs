---
type: docs
page_title: "Getting Started with Gerillass Sass Library"
page_description: "With Sass and Gerillass you can generate scalable CSS outputs, empower your frontend workflow, and create responsive websites quickly and easily."
---

# Getting Started

***
_This page is an overview of the Gerillass installation. To see the examples and learn how to use Gerillass, check the sidebar on the left-hand side._

**[Gerillass](https://gerillass.com)** is a library built on top of **[Sass (Syntactically Awesome Style Sheets)](https://sass-lang.com/)** to give you flexibility in your projects and to boost your performance and creativity.

Many of the utilities in Gerillass are solutions I came up with for the challenges I faced as a frontend developer over the years. Over time, these solutions were shaped by other popular libraries and frameworks such as **[Bourbon](https://www.bourbon.io/)**, **[Susy](https://www.oddbird.net/)**, **[Scut](https://davidtheclark.github.io/scut/)**, and **[Bootstrap](https://getbootstrap.com/)**, and they helped me create Gerillass.

I hope you enjoy using it!

<div class="download-buttons btn-wrapper" style="margin-bottom: 80px;">
    <a class="btn small" href="https://github.com/selfishprimate/gerillass" target="_blank" rel="noopener noreferrer">
        <ion-icon name="download-outline"></ion-icon>
        <span class="btn-text">Download the Library</span>
    </a>
    <a class="btn small" href="https://gerillass.com/" target="_blank" rel="noopener noreferrer">
        <ion-icon name="link-outline"></ion-icon>
        <span class="btn-text">Visit Gerillass Site!</span>
    </a>
</div>

## Dart Sass Upgrade
_We are saying goodbye to LibSass with version 1.3.0._

LibSass and the packages built on it, including Node Sass, are deprecated, so **Gerillass no longer supports LibSass as of version 1.3.0**. If you have a problem running Gerillass v1.3.0, please use Dart Sass instead of LibSass. If you are already running Dart Sass, you can safely install and use Gerillass 1.3.0 and later versions. If not, please use an earlier version.

## Installation

{{< highlightwrap class="terminal">}}
Install the library as a development dependency with npm:
{{< highlight nix >}}
npm install gerillass --save-dev
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
Or with Yarn:
{{< highlight nix >}}
yarn add gerillass --dev
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Then load it. If your setup resolves packages from **node_modules**, which Vite, webpack, Next.js and most modern bundlers do, this is all you need:
{{< highlight scss >}}
@use 'gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

### Using the pkg: importer

{{< highlightwrap >}}
If you call Dart Sass yourself rather than through a bundler, turn on its package importer and use a `pkg:` URL.
{{< highlight scss >}}
@use 'pkg:gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
In your build script:
{{< highlight js >}}
// Dart Sass 1.71.0 or later
import * as sass from 'sass';
import { NodePackageImporter } from 'sass';

sass.compile('style.scss', { importers: [new NodePackageImporter()] });
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
Or from the command line:
{{< highlight nix >}}
sass --pkg-importer=node style.scss style.css
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Pointing straight at the file always works too:
{{< highlight scss >}}
@use '{node_modules_path}/gerillass/scss/gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint warning >}}
**A note on eyeglass.** Gerillass still ships eyeglass module metadata, but eyeglass has not been released since June 2022 and its importer is broken with current Dart Sass. Any `@import` fails with `doneImporting is not a function`, whether Gerillass is involved or not. It also relies on the legacy JS API, which Dart Sass removes in 2.0.0. Use the `pkg:` importer above instead, which is the built-in equivalent.
{{< /hint >}}

{{< hint info >}}
The per-tool recipes below were each verified against a real build of Gerillass v1.5.0. The versions used are listed at the [end of this section](#versions-these-examples-were-tested-with).
{{< /hint >}}

### Using with Vite

{{< highlightwrap >}}
Vite resolves the package by name, so there is nothing to configure. This covers anything built on Vite, including React, Vue, Svelte, SvelteKit and Astro.
{{< highlight scss >}}
@use 'gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

### Using with webpack

{{< highlightwrap >}}
`sass-loader` also resolves the package by name, with no extra options.
{{< highlight scss >}}
@use 'gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

### Using with Next.js

{{< highlightwrap >}}
Next.js needs to be told where the library lives. In `next.config.mjs`:
{{< highlight js >}}
export default {
  sassOptions: {
    loadPaths: ["node_modules/gerillass/scss"],
  },
};
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Then, in any `.scss` file:
{{< highlight scss >}}
@use 'gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

### Using with Angular

{{< highlightwrap >}}
Add the library folder to the build target's options in `angular.json`. Angular calls this option `includePaths`, not `loadPaths`.
{{< highlight js >}}
"stylePreprocessorOptions": {
  "includePaths": ["node_modules/gerillass/scss"]
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Then, in `src/styles.scss`:
{{< highlight scss >}}
@use 'gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

### Using with Gulp

{{< hint info >}}
**Important:** `gulp-sass` hands its options straight to Dart Sass, so the option is **`loadPaths`**. The old `includePaths` name came from Node Sass and no longer resolves.
{{< /hint >}}

{{< highlightwrap >}}
{{< highlight js >}}
const { src, dest } = require("gulp");
const sass = require("gulp-sass")(require("sass"));

function styles() {
  return src("assets/sass/**/*.scss")
    .pipe(sass({ loadPaths: ["node_modules/gerillass/scss"] }).on("error", sass.logError))
    .pipe(dest("assets/css"));
}

exports.styles = styles;
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Then:
{{< highlight scss >}}
@use 'gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

### Using with Grunt

{{< hint info >}}
**Important:** Use `grunt-sass` with Dart Sass as the implementation. The option here is **`loadPaths`** as well, not `loadPath` and not `includePaths`.
{{< /hint >}}

{{< highlightwrap >}}
{{< highlight js >}}
module.exports = function (grunt) {
  grunt.loadNpmTasks("grunt-sass");
  grunt.initConfig({
    sass: {
      dist: {
        options: {
          implementation: require("sass"),
          loadPaths: ["node_modules/gerillass/scss"],
        },
        files: { "css/main.css": "src/main.scss" },
      },
    },
  });
};
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Then:
{{< highlight scss >}}
@use 'gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

### Cloning the repository from GitHub

{{< highlightwrap class="terminal">}}
You can clone the repository from GitHub to your computer.
{{< highlight nix >}}
git clone https://github.com/selfishprimate/gerillass.git
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
Or you can add the library as a submodule to your Git-based project ([What is a submodule?](https://git-scm.com/book/en/v2/Git-Tools-Submodules)).
{{< highlight nix >}}
git submodule add https://github.com/selfishprimate/gerillass.git
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Including it in your project:
{{< highlight scss >}}
@use '{folder_path}/gerillass/scss/gerillass' as *;
{{< /highlight >}}
{{< /highlightwrap >}}

### Versions these examples were tested with

<div class="table">
  <table>
    <thead>
      <tr>
        <th>Tool</th>
        <th>Version</th>
      </tr>
    </thead>
    <tbody>
      <tr><td class="name">Dart Sass</td><td class="type">1.103.1</td></tr>
      <tr><td class="name">Vite</td><td class="type">8.2.2</td></tr>
      <tr><td class="name">webpack / sass-loader</td><td class="type">5.110.3 / 17.0.1</td></tr>
      <tr><td class="name">Next.js</td><td class="type">16.3.4</td></tr>
      <tr><td class="name">Angular CLI</td><td class="type">20.3.36</td></tr>
      <tr><td class="name">Gulp / gulp-sass</td><td class="type">5.0.1 / 6.0.1</td></tr>
      <tr><td class="name">Grunt / grunt-sass</td><td class="type">1.6.3 / 4.1.0</td></tr>
    </tbody>
  </table>
</div>

## Using Gerillass with an AI coding agent

Gerillass ships two files that let a coding agent use the library correctly instead of guessing at it. Both are inside the installed package, so an agent working in your project can read them straight out of `node_modules/gerillass/`.

**`gerillass.json`** describes every mixin and function: its signature, what each argument accepts, examples that compile, and inputs that are refused.

{{< highlightwrap >}}
{{< highlight js >}}
const api = require("gerillass/gerillass.json");
{{< /highlight >}}
{{< /highlightwrap >}}

**`SKILL.md`** is a written guide generated from that manifest: how to load the library, the full catalogue, and the argument forms that are easy to get wrong. If your agent supports [Agent Skills](https://code.claude.com/docs/en/skills), copy it into your skills folder.

{{< highlightwrap class="terminal">}}
{{< highlight nix >}}
mkdir -p .claude/skills/gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
{{< highlight nix >}}
cp node_modules/gerillass/SKILL.md .claude/skills/gerillass/
{{< /highlight >}}
{{< /highlightwrap >}}

Otherwise, point your agent at the file and it will read it as plain Markdown.

Neither file is written by hand. Signatures are parsed from the Sass sources, and every example and refusal in the manifest is executed by the test suite, so what the manifest says the library does is what the library does.

## Three ways to call the same mixin

None of them is required. Pick whichever reads best in your project, and stay with it in a given file. All three produce identical CSS.

{{< highlightwrap >}}
**Bare.** The shortest, and fine unless another library defines the same name.
{{< highlight scss >}}
@use 'gerillass' as *;

.avatar {
  @include circle(50px);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
**With the `gls-` prefix.** Every mixin also answers to a prefixed name, which avoids collisions with Bootstrap and friends.
{{< highlight scss >}}
@use 'gerillass' as *;

.avatar {
  @include gls-circle(50px);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
**Through a namespace.** This is Sass's own mechanism and the tidiest of the three, because nothing enters your global scope at all, so a collision is impossible. The name after `as` is yours to choose.
{{< highlight scss >}}
@use 'gerillass' as gls;

.avatar {
  @include gls.circle(50px);
}
{{< /highlight >}}
{{< /highlightwrap >}}

The `gls-` prefix predates the Sass module system. If you are starting fresh, the namespace does the same job without the extra name.

## Vendor Prefix Support

Bundlers such as [Gulp](https://gulpjs.com/), [Grunt](https://gruntjs.com/) and [webpack](https://webpack.js.org/) are so widely used, and they run plugins like Autoprefixer to handle vendor prefixes, that Gerillass does not provide vendor prefix support of its own.

Feel free to use any tool for that. My suggestion is Autoprefixer. If you are not using one of the bundlers mentioned above, you can also add vendor prefixes by hand with the [Autoprefixer CSS Online](https://autoprefixer.github.io/) tool.

## Experimenting

Experimenting with Gerillass is easy. If you already process Sass files on your computer, [download the Gerillass Sass library](https://github.com/selfishprimate/gerillass/archive/main.zip), include it in your project, and start using it. If not, use [Gerillass Play](https://github.com/selfishprimate/gerillass-play)! Gerillass Play is a Gulp-based playground that helps you get started with [Sass](https://sass-lang.com/) and [Gerillass](https://gerillass.com/) quickly.

{{< hint info >}}
**Important Note**: Don't forget that you must have [**Node.js**](https://nodejs.org/en/) and [**Gulp CLI**](https://gulpjs.com/docs/en/getting-started/quick-start) installed on your machine to work with Gerillass Play.
{{< /hint >}}

## Testing

Gerillass comes with a unit-testing module named [True](https://github.com/oddbird/true), which makes Sass unit tests possible (endless thanks to the [OddBird Team](https://github.com/oddbird)).

You can find two test examples in the `test` folder. Take your time, examine the code, and then write your own unit tests. After that, run the following command to see if the tests pass.

{{< highlightwrap class="terminal">}}
{{< highlight nix >}}
npm test
{{< /highlight >}}
{{< /highlightwrap >}}
