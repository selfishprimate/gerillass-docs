---
title: "Resizable"
site_title: "Resizable Sass Mixin"
site_description: "Resizable Sass mixin helps you to make an element resizable on both horizontal or vertical directions."
site_keywords: "Resizable Sass Mixin, Sass Resize, SCSS Resize, CSS Resizable, SCSS to CSS, Sass to CSS"
---

# Resizable

{{< mixin type="Mixin" name="resizable" >}}
**Resizable** Sass mixin helps you to make an element resizable on both horizontal or vertical directions.
{{< /mixin >}}

{{< hint info >}}
**Note:** This property doesn't work with inline elements and block elements for which the `overflow` property is set to `visible`.
{{< /hint >}}

## Arguments

{{< arguments/table footnote="">}}
  {{< arguments/row name="$direction" type="string" description="This option sets the direction of the resize property. Accepts `both`, `horizontal`, `vertical`, `none` values. The default value is set to `both`." >}}
  {{< arguments/row name="$overflow" type="string" description="This option adjust the `overflow` property. Default value is set to `auto`. " >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments. 
{{< hint info >}}
A tiny icon will appear in the lower right corner of the box below, grab it and try resizing the box.
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

