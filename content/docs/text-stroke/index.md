---
title: "Text Stroke"
page_title: "Text Stroke Sass Mixin"
page_description: "Text Stroke Sass mixin helps you to add stroke to a text element and style it very easily."
page_keywords: "CSS text Stroke, Sass Text Stroke, CSS Text Stroke Generator, CSS Text Stroke Property, CSS Text Stroke Inside, CSS Text Stroke Width, CSS Text Stroke Animation, CSS Text Stroke Fallback Color, CSS Text Stroke Color, CSS Text Stroke Fill Color"
---

# Text Stroke

{{< mixin type="Mixin" name="text-stroke" >}}
**Text Stroke Sass mixin** helps you to add stroke to a text element and style it very easily.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="**Design Tip:** When your stroke color is dark try to make the fallback color the same to make the text look more consistent with the rest of the design.">}}
  {{< arguments/row name="$color" type="color" description="Sets the color of a text. The default color value is set to transparent." >}}
  {{< arguments/row name="$stroke-color" type="color" description="Sets the stroke color of a text. The default stroke color value is black." >}}
  {{< arguments/row name="$fallback-color" type="color" description="This option is for non-supporting browsers. It will prevent text to disappear entirely in non-supporting browsers. The default value is black." >}}
  {{< arguments/row name="$stroke-width" type="number (with unit)" description="Sets the width of the stroke. You can pass `thin`, `medium`, `thick` values as a string as well to set the width of the stroke." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any argument. 
{{< highlight scss >}}
.element {
  @include text-stroke;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  color: black;
  -webkit-text-fill-color: transparent;
  -webkit-text-stroke-color: black;
  -webkit-text-stroke-width: 1px;
}
{{< /highlight >}}
<h1 style="margin: 0;color: black;-webkit-text-fill-color: transparent;-webkit-text-stroke-color: black;-webkit-text-stroke-width: 1px;">Text Stroke is Awesome!</h1>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now pass some arguments to make the text look sexier!
{{< highlight scss >}}
.element {
  @include text-stroke(
    $color: azure,
    $stroke-color: cadetblue,
    $fallback-color: cadetblue,
    $stroke-width: 1px
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  color: cadetblue;
  -webkit-text-fill-color: azure;
  -webkit-text-stroke-color: cadetblue;
  -webkit-text-stroke-width: 1px;
}
{{< /highlight >}}
<h1 style="margin: 0;color: cadetblue;-webkit-text-fill-color: azure;-webkit-text-stroke-color: cadetblue;-webkit-text-stroke-width: 1px;">Text Stroke is Awesome!</h1>
{{< /highlightwrap >}}

