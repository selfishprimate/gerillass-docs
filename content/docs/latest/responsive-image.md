---
title: "Responsive Image"
---

# Responsive Image
{{< mixin type="Mixin" name="responsive-image" >}}
**Responsive Image** Sass mixin helps you to make images responsive and reset the default `display: inline;` propert to `display: block;` to romove the extra space below them.
{{< /mixin >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in a selector that targets the `<image>` element itself.
{{< highlight scss >}}
img{
    @include gls-responsive-image;
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

