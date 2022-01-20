---
title: "Adaptive"
site_title: "Adaptive Sass Mixin"
site_description: "Adaptive Sass mixin helps you set a max-width value to the containing elements. It is useful when you wish to apply adaptive design concepts to your responsive designs."
site_keywords: "Adaptive Design, CSS Adaptive Design, Bootstrap Adaptive Design, Adaptive Design with Sass, SCSS Adaptive Design, What is Adaptive Design?, "
---

# Adaptive

{{< mixin type="Mixin" name="adaptive" >}}
**Adaptive** Sass mixin helps you to set `max-width` value to the containing elements based on the `breakpoint` values defined in the `_map-for-breakpoints.scss` file, and also specifies a `$gutter` value, where the edges of a browser screen can most closely get to the edges of the selected element.
{{< hint info >}}
**Tip:** Adaptive mixin works best with the `percentage` values.
{{< /hint >}}
{{< /mixin >}}

## What is Adaptive Design?

**Adaptive design** is a graphical user interface design that responds differently to various device screen sizes. Adaptive design typically uses multiple fixed layout sizes and when it detects the device size, it selects the best layout for this specific screen size.

As for the **Adaptive Sass mixin**, it provides the fastest and most consistent adaptive design option for you.

## Arguments

{{< arguments/table footnote="Apply this mixin to your containing element of your layout, and then narrow or widen your browser screen to test it!">}}
  {{< arguments/row name="$gutter" type="number (with unit)" description="Accepts only one value and sets it for all the breakpoints. The default value is set to `30px`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments. Default `$gutter` value is `30px`.
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
Try passing an argument value with `em` unit (you can use any kind of length units here: `px`, `em`, `rem`, `percentage` etc. will be just fine).
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
    ax-width: calc(576px - (2em * 2));
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