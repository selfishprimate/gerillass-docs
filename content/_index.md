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

{{< highlight nix >}}
npm install gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
You can **import** Gerillass with the **node_modules** path.
{{< highlight scss >}}
@import '{node_modules_path}/gerillass/scss/gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}

**To include the library without using the {node_modules_path}, see the examples below.**

{{< highlightwrap >}}
If you're working with an **eyeglass** setup, simply import it without providing the **node_modules** path.
{{< highlight scss >}}
@import 'gerillass';
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
@import 'gerillass/scss/gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}

### Node.js Installation

If you are working on a Node project, you can install Gerillass as a dependency.

{{< highlightwrap class="terminal">}}
**npm installation**
{{< highlight nix >}}
npm install gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
**Yarn installation**
{{< highlight nix >}}
yarn add gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

### Using with React.js

{{< highlightwrap >}}
Simply `@import` the library at the beginning of your App.scss file without using the **node_modules** path.
{{< highlight scss >}}
@import 'gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}

### Using with Gulp

{{< highlightwrap >}}
You can add a new Gulp task like the one below, or simply add the `includePaths: ['node_modules/gerillass/scss']` option to a task you already have.
{{< highlight js >}}
function sassify(done) {
  return (
    src("assets/sass/**/*.scss")
    .pipe(sass({
      outputStyle: "expanded",
      includePaths: ["node_modules/gerillass/scss"],
    }).on('error', sass.logError))
    .pipe(dest("assets/css"))
  );
  done()
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Including it in your project:
{{< highlight scss >}}
@import 'gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}
    
### Using with Grunt

{{< highlightwrap >}}
You can add the Gerillass library by editing your Gruntfile.js at the root level of your project. Simply find the rules for Sass and add `loadPath: ['node_modules/gerillass/scss']` inside the `options` object.
{{< highlight js >}}
sass: {
  dist: {
    options: {
      style: "expanded",
      loadPath: ['node_modules/gerillass/scss']
    },
    files: {
      "main.css": "main.scss"
    }
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Including it in your project:
{{< highlight scss >}}
@import 'gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}

## Experimenting

Experimenting with Gerillass is easy. If you already process Sass files on your computer, [download the Gerillass Sass library](https://github.com/selfishprimate/gerillass/archive/refs/tags/v1.2.2.zip), include it in your project, and start using it. If not, use [Gerillass Play](https://github.com/selfishprimate/gerillass-play)! Gerillass Play is a Gulp-based playground that helps you get started with [Sass](https://sass-lang.com/) and [Gerillass](https://gerillass.com/) quickly.

{{< hint info >}}
**Important Note**: Don't forget that you must have [**Node.js**](https://nodejs.org/en/) and [**Gulp**](https://gulpjs.com/docs/en/getting-started/quick-start) installed globally on your machine.
{{< /hint >}}

## Testing

Gerillass comes with a unit-testing module named [True](https://github.com/oddbird/true), which makes Sass unit tests possible (endless thanks to the [OddBird Team](https://github.com/oddbird)).

You can find two test examples in the `test` folder. Take your time, examine the code, and then write your own unit tests. After that, run the following command to see if the tests pass.

{{< highlightwrap class="terminal">}}
{{< highlight nix >}}
npm test
{{< /highlight >}}
{{< /highlightwrap >}}

