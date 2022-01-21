---
title: "Responsive Image"
page_title: "Responsive Image Sass Mixin"
page_description: "Responsive Image Sass mixin helps you to make images responsive and change the default display CSS property value from inline to block in order to remove the extra space below them."
page_keywords: "CSS Responsive Image, Sass Responsive Image, Responsive Images, Reset CSS Image, CSS Fluid Images, Responsive img tag"
---

# Responsive Image

{{< mixin type="Mixin" name="responsive-image" >}}
**Responsive Image Sass mixin** helps you to make images responsive and change the default `display` CSS property value from `inline` to `block` in order to remove the extra space below them.
{{< /mixin >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in a selector that targets the `<img>` element itself.
{{< highlight scss >}}
img {
  @include responsive-image;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
img {
  display: block;
  width: 100%;
}
{{< /highlight >}}
{{< /highlightwrap >}}

