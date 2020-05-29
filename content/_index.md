---
title: Introduction
type: docs
---

# Strongest Sass Toolkit ever!

Hi developers, designers and the other enthusiasts of the open-source community! 

I am proud to present to you a brand new toolkit named [**Gerillass**](https://gerillass.com/). It is an open-source toolkit that contains a set of Sass mixins to help you avoid code repetition and generate better, faster and consistent CSS code.

**More than anything, Gerillass is here to make web development fun for everyone.**

Hope you'll enjoy using it!

<div class="download-buttons btn-wrapper" style="margin-bottom: 80px;">
    <a class="btn small" href="https://github.com/babilkuyusu/gerillass" target="_blank">
        <ion-icon name="download-outline"></ion-icon>
        <span class="btn-text">Download the Library</span>
    </a>
    <a class="btn small" href="https://gerillass.com/" target="_blank">
        <ion-icon name="link-outline"></ion-icon>
        <span class="btn-text">Visit Gerillass Site!</span>
    </a>
</div>

## What is Gerillass?

Gerillass is a library built on top of [**Sass (Syntactically Awesome Style Sheets)**](https://sass-lang.com/) to give you flexibility for your projects and accelerate your performance and creativity.

Many of the utilities that come with Gerillass are the solutions I have come up with for the challenges I have faced as a frontend developer over the years. These solutions have been shaped by the inspiration of other popular libraries and frameworks like [**Bourbon**](https://www.bourbon.io/), [**Scut**](https://davidtheclark.github.io/scut/), [**Compass**](http://compass-style.org/), [**Bootstrap**](https://getbootstrap.com/), etc. over time and helped me create Gerillass.

## Installation

You can Install Gerillass via [**Github**](https://github.com/babilkuyusu/gerillass), [**npm (Node Package Manager)**](https://www.npmjs.com/), [**Yarn**](https://yarnpkg.com/) by **using terminal window**, and include the source files into your projects. Or you can [**download it manually**](https://github.com/babilkuyusu/gerillass/archive/master.zip) into your local computer.

### 1. Github

{{< highlightwrap class="terminal">}}
Open the terminal window. Target the folder that you want Gerillass to be installed. Copy and past the command below and hit the enter to install the library into your local computer.
{{< highlight nix >}}
git clone https://github.com/babilkuyusu/gerillass.git
{{< /highlight >}}

If you're running on a Git project you can add Gerillass as a subdirectory to your Git repository.
{{< highlight nix >}}
git submodule add https://github.com/babilkuyusu/gerillass.git
{{< /highlight >}}
{{< /highlightwrap >}}


### 2. RubyGems

Install the Gerillass gem by using the RubyGems package manager:

{{< highlightwrap class="terminal">}}
{{< highlight nix >}}
gem install gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

Install the Gerillass library into the current directory:

{{< highlightwrap class="terminal">}}
{{< highlight nix >}}
gerillass install
{{< /highlight >}}
{{< /highlightwrap >}}

**Tip:** You can target installation into a specific directory using the path flag:

{{< highlightwrap class="terminal">}}
{{< highlight nix >}}
gerillass install --path my/custom/path/
{{< /highlight >}}
{{< /highlightwrap >}}

Import Gerillass at the beginning of your style sheet:

{{< highlightwrap >}}
{{< highlight scss >}}
@import "gerillass/core/gerillass";
{{< /highlight >}}
{{< /highlightwrap >}}

### 3. Installation for Ruby on Rails

{{< highlightwrap class="terminal">}}
Add Gerillass to your Gemfile:
{{< highlight nix >}}
gem install gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
After that run the command below:
{{< highlight nix >}}
bundle install
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
Restart your server and rename application.css to application.scss:
{{< highlight nix >}}
mv app/assets/stylesheets/application.css app/assets/stylesheets/application.scss
{{< /highlight >}}
{{< /highlightwrap >}}

Delete all Sprockets directives in application.scss (require, require_tree and require_self) and use Sass’s native @import instead (why?).

{{< highlightwrap >}}
Import Gerillass at the beginning of application.scss. Any project styles that utilize Gerillass’s features must be imported after Gerillass.
{{< highlight scss >}}
@import "gerillass";
@import "home";
@import "users";
{{< /highlight >}}
{{< /highlightwrap >}}

### 3. Node.js

If you are working on a Node.js project you can add Gerillass as a dependency.

{{< highlightwrap class="terminal">}}
**npm installation:**
{{< highlight nix >}}
npm install gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="terminal">}}
**Yarn installation:**
{{< highlight nix >}}
yarn add gerillass
{{< /highlight >}}
{{< /highlightwrap >}}

### 5. How to Include?

{{< highlightwrap class="no-lang">}}
Import Gerillass at the beginning of your stylesheet.
{{< highlight scss >}}
@import "gerillass/core/gerillass";
{{< /highlight >}}
{{< /highlightwrap >}}

## Contribution

So, if you you like Gerillass and you want to help with this documentation page please feel free to contribute to the project.

## Related Links

1. [**Gerillass Site**]()
2. [**Github**]()
3. [**Change Log**]()
4. [**Blog**]()