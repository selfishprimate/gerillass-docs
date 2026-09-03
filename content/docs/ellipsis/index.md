---
title: "Ellipsis"
page_title: "Ellipsis Sass Mixin"
page_description: "The Ellipsis Sass mixin helps you trim text and add an ellipsis at the end of it using the CSS text-overflow property."
---

# Ellipsis

{{< mixin type="Mixin" name="ellipsis" >}}
The **Ellipsis** Sass mixin helps you truncate text and add an **ellipsis** at the end of it, based on the given `$width` value.
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$width (100%)" type="number <br/>(with unit)" description="The `max-width` of the selected element before its text is truncated." >}}
  {{< arguments/row name="$display (inline-block)" type="string" description="Sets the `display` property of the selected elements. The default value is `inline-block`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin inside an element's selector to truncate the text in it.
{{< highlight scss >}}
.element{
  @include ellipsis;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  display: inline-block;
  max-width: 100%;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
  word-wrap: normal;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Change the `$width` or `$display` values if you need to.
{{< highlight scss >}}
.element{
  @include ellipsis(
    $width: 200px,
    $display: block
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  display: block;
  max-width: 200px;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
  word-wrap: normal;
}
{{< /highlight >}}
{{< /highlightwrap >}}
