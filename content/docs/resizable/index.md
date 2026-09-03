---
title: "Resizable"
page_title: "Resizable Sass Mixin"
page_description: "The Resizable Sass mixin helps you make an element resizable in both the horizontal and vertical directions."
page_keywords: "Resizable Sass Mixin, Sass Resize, SCSS Resize, CSS Resizable, SCSS to CSS, Sass to CSS"
---

# Resizable

{{< mixin type="Mixin" name="resizable" >}}
The **Resizable** Sass mixin helps you make an element resizable in both the horizontal and vertical directions.
{{< /mixin >}}

{{< hint info >}}
**Note:** This property doesn't work on inline elements, or on block elements whose `overflow` property is set to `visible`.
{{< /hint >}}

## Arguments

{{< arguments/table footnote="">}}
  {{< arguments/row name="$direction" type="string" description="Sets the direction of the `resize` property. Accepts the values `both`, `horizontal`, `vertical`, and `none`. The default value is `both`." >}}
  {{< arguments/row name="$overflow" type="string" description="Sets the `overflow` property. The default value is `auto`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments. 
{{< hint info >}}
A tiny icon will appear in the lower right corner of the box below. Grab it and try resizing the box.
{{< /hint >}}
{{< highlight scss >}}
.element{
  @include resizable;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  resize: both;
  overflow: auto;
  max-width: 100%;
}
{{< /highlight >}}
{{< sandbox class="small" >}}
resize: both;overflow: auto;max-width: 100%;background-image: repeating-linear-gradient(-45deg, crimson 0, crimson 1em, pink 1em, pink 2em);
{{< /sandbox >}}
{{< /highlightwrap >}}

