---
title: "Reset Figure"
site_title: "Reset Figure Sass Mixin"
site_description: "Reset Figure Sass mixin helps you to reset the margin values of <figure> elements to zero and make the <img> element responsive in it."
site_keywords: "HTML Figure Element, Responsive Figure Element, Responsive Image, CSS Responsive Image, CSS Figure Responsive, Responsive Image CSS, Responsive Images"
---

# Reset Figure
{{< mixin type="Mixin" name="reset-figure" >}}
**Reset Figure Sass mixin** helps you to reset the margin values of `<figure>` elements to `0` and make the `<img>` element responsive (fluid) in it, that is it sets the width CSS property of the `<img>` element to `100%`.
{{< /mixin >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in a selector that targets the `<figure>` element itself.
{{< highlight scss >}}
figure{
  @include reset-figure;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
figure {
  margin: 0;
}
figure img {
  display: block;
  width: 100%;
}
{{< /highlight >}}
{{< /highlightwrap >}}

