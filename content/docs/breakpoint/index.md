---
title: "Breakpoint"
page_title: "Create Breakpoints and CSS Media Queries with Sass and Gerillass"
page_description: "The Breakpoint Sass mixin helps you create scalable media queries and breakpoints using the @media CSS at-rule in SCSS."
page_keywords: "CSS Breakpoints, CSS Breakpoints 2021, CSS Breakpoints Bootstrap, CSS Breakpoints for Mobile Devices, CSS Breakpoints List, Sass Breakpoints, CSS Breakpoints 2022, CSS Media Queries, Sass Media Queries, CSS Breakpoints for Responsive Design, Sass Include Breakpoint, Sass Breakpoint Mixin"
---

# Breakpoint

{{< mixin type="Mixin" name="breakpoint" >}}
The **Breakpoint** Sass mixin helps you create scalable media queries and breakpoints using the [@media CSS at-rule](https://developer.mozilla.org/en-US/docs/Web/CSS/@media) in SCSS.

{{< hint info >}}
**Tip:** There are predefined values for breakpoints in the `_map-for-breakpoints.scss` file based on Bootstrap's breakpoint values. **You can add more values here to expand the list or replace existing ones with yours**.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="When you use the `between` option you must pass two values for `width`, and they must be separated by a space. See the [examples](#examples) for more.">}}
  {{< arguments/row name="$mode" type="string" description="Sets the `width` media feature. Accepts the values `only`, `min`, `max`, and `between`." >}}
  {{< arguments/row name="$value" type="number (with unit)" description="The width value at which your styles will be applied." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin and **pass a custom value** to it. The code below will apply styles only if your browser's viewport is equal to `320px`.
{{< highlight scss >}}
.element{
  @include breakpoint(320px) {
    background-color: green;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (width: 320px) {
  .element {
    background-color: green;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
If you set the `$mode` option to `only`, you will see that the result is similar to the first example. The code below will apply styles only if your browser's viewport is equal to `1200px`.
{{< highlight scss >}}
.element{
  @include breakpoint(only, 1200px) {
    background-color: teal;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (width: 1200px) {
  .element {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's set the `$mode` option to `min` and pass a predefined breakpoint value. If you are a **mobile-first** person, you are going to use this one a lot!
{{< highlight scss >}}
.element{
  @include breakpoint(min, medium) {
    background-color: green;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 768px) {
  .element {
    background-color: green;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
For **desktop-first** arrangements, set the `$mode` option to `max`. This time, let's pass a custom value for the second argument.
{{< highlight scss >}}
.element{
  @include breakpoint(max, 1024px) {
    background-color: green;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (max-width: 1024px) {
  .element {
    background-color: green;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
We can set a range between two values to apply our styles.
{{< hint info >}}
**Tip:** You can use **predefined** and **custom** values together if you like.
{{< /hint >}}
{{< highlight scss >}}
.element{
  @include breakpoint(between, small 1200px) {
    background-color: green;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 576px) and (max-width: 1200px) {
  .element {
    background-color: green;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
**Note that** when you use the `between` mode with predefined values, the `max-width` value is always reduced by one. **This prevents the styles you apply from overlapping each other.**
{{< hint info >}}
**Important:** Please examine how the predefined breakpoint values line up against each other in the code below.
{{< /hint >}}

{{< highlight scss >}}
.element{
  @include breakpoint(between, small medium) {
    background-color: green;
  };
  @include breakpoint(between, medium large) {
    background-color: blue;
  };
  @include breakpoint(between, large xlarge) {
    background-color: purple;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 576px) and (max-width: 767px) {
  .element {
    background-color: green;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .element {
    background-color: blue;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .element {
    background-color: purple;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
**Reducing by one** only happens with **predefined** values. When you work with custom values, you don't have to worry about it!
{{< highlight scss >}}
.element{
  @include breakpoint(between, small 1199px) {
    background-color: green;
  };
  @include breakpoint(between, 1200px 1400px) {
    background-color: blue;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 576px) and (max-width: 1199px) {
  .element {
    background-color: green;
  }
}
@media (min-width: 1200px) and (max-width: 1400px) {
  .element {
    background-color: blue;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
**Now let's define a range without passing the `between` option.** Simply pass two values and **separate them with a comma**. 
{{< hint info >}}
The values can be either custom numbers (with a unit) or predefined values.
{{< /hint >}}
{{< highlight scss >}}
.element{
  @include breakpoint(320px, 768px) {
    background-color: teal;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 320px) and (max-width: 768px) {
  .element {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try it with the predefined values just to see that it works.
{{< highlight scss >}}
.element{
  @include breakpoint(small, large) {
    background-color: teal;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 576px) and (max-width: 991px) {
  .element {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}