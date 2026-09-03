---
title: "Adaptive"
page_title: "Adaptive Sass Mixin"
page_description: "The Adaptive Sass mixin helps you set a max-width value on your container elements. It is useful when you want to apply adaptive design concepts to your responsive designs."
page_keywords: "Adaptive Design, CSS Adaptive Design, Bootstrap Adaptive Design, Adaptive Design with Sass, SCSS Adaptive Design, What is Adaptive Design?"
---

# Adaptive

{{< mixin type="Mixin" name="adaptive" >}}
The **Adaptive Sass mixin** helps you set a `max-width` value on your container elements, based on the `breakpoint` values defined in the `_map-for-breakpoints.scss` file. It also takes a `$gutter` value, which sets how close the edges of the browser screen can get to the edges of the selected element.
{{< hint info >}}
**Tip:** The Adaptive mixin works best with `percentage` values.
{{< /hint >}}
{{< /mixin >}}

## What is Adaptive Design?

**Adaptive design** is a graphical user interface design approach that responds differently to various device screen sizes. It typically uses several fixed layout sizes, and when it detects the device size, it selects the best layout for that specific screen size.

The **Adaptive Sass mixin** gives you the fastest and most consistent way to apply adaptive design.

## Arguments

{{< arguments/table footnote="Apply this mixin to the container element of your layout, then narrow or widen your browser window to test it!">}}
  {{< arguments/row name="$gutter" type="number (with unit)" description="Accepts one value and applies it to all the breakpoints. The default value is `30px`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments. The default `$gutter` value is `30px`.
{{< highlight scss >}}
.main-container{
  @include adaptive;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.main-container {
  margin: 0 auto;
}
@media (min-width: 576px) {
  .main-container {
    max-width: calc(576px - (30px * 2));
  }
}
@media (min-width: 768px) {
  .main-container {
    max-width: calc(768px - (30px * 2));
  }
}
@media (min-width: 992px) {
  .main-container {
    max-width: calc(992px - (30px * 2));
  }
}
@media (min-width: 1200px) {
  .main-container {
    max-width: calc(1200px - (30px * 2));
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Try passing a value with an `em` unit. You can use any length unit here, so `px`, `em`, `rem`, and percentages all work.
{{< highlight scss >}}
.main-container{
  @include adaptive(2em);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.main-container {
  margin: 0 auto;
}
@media (min-width: 576px) {
  .main-container {
    max-width: calc(576px - (2em * 2));
  }
}
@media (min-width: 768px) {
  .main-container {
    max-width: calc(768px - (2em * 2));
  }
}
@media (min-width: 992px) {
  .main-container {
    max-width: calc(992px - (2em * 2));
  }
}
@media (min-width: 1200px) {
  .main-container {
    max-width: calc(1200px - (2em * 2));
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}
