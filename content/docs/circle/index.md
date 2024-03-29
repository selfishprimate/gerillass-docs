---
title: "Circle"
page_title: "Circle Sass Mixin"
page_description: "Circle Sass Mixin helps you to create a perfect circle shape in CSS and Sass."
---

# Circle

{{< mixin type="Mixin" name="circle" >}}
**Circle** Sass mixin helps you to easily create perfect circle shapes.
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$size" type="string" description="The size of the circle." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Call the mixin in a selector and pass a number value (with unit) for the `$size` argument.
{{< highlight scss >}}
.element{
  @include circle(150px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  width: 150px;
  height: 150px;
  display: inline-block;
  border-radius: 100%;
}
{{< /highlight >}}
{{< /highlightwrap >}}




