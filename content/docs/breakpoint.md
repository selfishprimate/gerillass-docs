---
title: "Breakpoint"
site_title: "Create Breakpoints and CSS Media Queries with Sass and Gerillass"
site_description: "Breakpoint Sass mixin helps you to create scalable media queries and breakpoints by using the @media CSS at-rule in SCSS."
---

# Breakpoint

{{< mixin type="Mixin" name="breakpoint" >}}
**Breakpoint** Sass mixin helps you to create scalable media queries and breakpoints by using the [@media CSS at-rule](https://developer.mozilla.org/en-US/docs/Web/CSS/@media) in SCSS.

{{< hint info >}}
**Tip:** There are predefined values for breakpoints in the `_map-for-breakpoints.scss` file based on Bootstraps' breakpoint values. **You can add more values here to expand the list or replace existing ones with yours**.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="When you use `between` option you must pass two values for `width` and they must be seperated by space. For more see the [examples](#examples).">}}
  {{< arguments/row name="$mode" type="string" description="Sets the `width` media feature. Accepts `only`, `min`, `max` or `between` values." >}}
  {{< arguments/row name="$value" type="number (with unit)" description="The width value to which your styles will be applied." >}}
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
If you set the `$mode` option to `only` you'll see that the result will be as similar as the first example. The code below will apply styles only if your browser's viewport is equal to `1200px`.
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
Now, let's set the `$mode` option to `min` and pass a predefined breakpoint value. If you are a **mobile-first** person you are going to use this one a lot!
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
For **desktop-first** arrangements set the `$mode` option to `max` and this time let's pass a custom value for the second argument.
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
We can set a range between two values ​​to apply our styles.
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
**Note that** when using the `between` mode with predefined values, the `max-width` value will always be extracted by one. **This setting prevents the styles ​​you apply from overlapping each other**.
{{< hint info >}}
**Important:** Please, examine how predefined breakpoint values ​​bounce among themselves correctly in the code below.
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
**Extracting by one** is only for **predefined** values. When you work with custom values you don't have to worry about that!
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
**Now let's try to define a range without passing the "between" option**. Simply pass two values and **seperate them by comma**. 
{{< hint info >}}
The values either can be custom numbers (with a unit) or predefined values.
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