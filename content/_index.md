---
type: docs
title: "Getting Started"
---

# Getting Started

***
_This page is an overview of the Gerillass installation. To see the examples and learn how to use Gerillass, check the sidebar at the left-hand side._

[Gerillass](https://gerillass.com) is a library built on top of [Sass (Syntactically Awesome Style Sheets)](https://sass-lang.com/) to give you flexibility for your projects and accelerate your performance and creativity.

Many of the utilities that come with Gerillass are the solutions I have come up with for the challenges I have faced as a frontend developer over the years. These solutions have been shaped by the inspiration of other popular libraries and frameworks like [Bourbon](https://www.bourbon.io/), [Susy](https://www.oddbird.net/), [Scut](https://davidtheclark.github.io/scut/), [Bootstrap](https://getbootstrap.com/), etc. over time and helped me create Gerillass.

Hope you’ll enjoy using it!

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

## Installation

{{< highlightwrap class="terminal">}}

{{< highlight nix >}}
npm install gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
You can **import** Gerillass with **node_modules** path.
{{< highlight scss >}}
@import '{node_modules_path}/gerillass/scss/gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}

**To include the library without using the {node_modules_path} see the examples below.**

{{< highlightwrap >}}
If you're working with an **eyeglass** setup, simply import it without providing the **node_modules** path.
{{< highlight scss >}}
@import 'gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}
    
### Cloning the repository from Github

{{< highlightwrap class="terminal">}}
You can clone the repository into your local computer from Github.
{{< highlight nix >}}
git clone https://github.com/selfishprimate/gerillass.git
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
Or you can add the library as a submodule into your Git based project ([What is a submodule?](https://git-scm.com/book/en/v2/Git-Tools-Submodules)).
{{< highlight nix >}}
git submodule add https://github.com/selfishprimate/gerillass.git
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Including to the project:
{{< highlight scss >}}
@import 'gerillass/scss/gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}

### Node.js Installation

If you are working on a Node project you can install Gerillass as a dependency.

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
You can add a new Gulp task as in the below example or simply add `includePath: ['node_modules/gerillass/scss']` option to the task if you have one already.
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
Including to the project:
{{< highlight scss >}}
@import 'gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}
    
### Using with Grunt

{{< highlightwrap >}}
You can add the Gerillass library by editing your Gruntfile.js at the root level of your project. Simply find the sass related rules and add `loadPath: ['node_modules/gerillass/scss']` inside the `options` object.
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
Including to the project:
{{< highlight scss >}}
@import 'gerillass';
{{< /highlight >}}
{{< /highlightwrap >}}

## Experimenting Gerillass

Experimenting Gerillass is easy. You can [**download the Gerillass library**](https://github.com/selfishprimate/gerillass/archive/master.zip), include it in your project, or use [**Gulpazan**](https://github.com/selfishprimate/gulpazan). Gulpazan is a Gulp based workflow, and it comes with Gerillass and all the packages and configurations that you'll need to work with Sass. [**Learn how you can install Gulpazan**](https://github.com/selfishprimate/gulpazan).

{{< hint info >}}
**Important Note**: Don't forget that you must have [**Node.js**](https://nodejs.org/en/) and [**Gulp**](https://gulpjs.com/docs/en/getting-started/quick-start) installed globally on your machine.
{{< /hint >}}

