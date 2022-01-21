---
title: "Ellipsis"
page_title: "Ellipsis Sass Mixin"
page_description: "Ellipsis Sass mixin helps you to trim a text and adds an ellipsis at the end of it by using CSS text-overflow property."
---

# Ellipsis

{{< mixin type="Mixin" name="ellipsis" >}}
**Ellipsis** Sass mixin helps you to truncate a text and adds an **ellipsis** at the end of it based on the given `$width` value.
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$width (100%)" type="number <br/>(with unit)" description="The `max-width` of the selected element before beign truncated." >}}
  {{< arguments/row name="$display (inline-block)" type="string" description="Sets the value of the `display` property of the selected element(s) to `inline-block`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in an element to truncate the text inside of it.
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
Change the `$width` or `$display` values of the selected element(s) if you need to.
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
