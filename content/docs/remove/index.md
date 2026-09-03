---
title: "Remove"
page_title: "Remove Sass Mixin"
page_description: "The Remove Sass mixin helps you set the display CSS property of an element to none. It combines that with CSS media queries to show or hide an element in the document flow at different device widths."
---

# Remove

{{< mixin type="Mixin" name="remove" >}}
The **Remove Sass mixin** helps you set the `display` CSS property of an element to `none`. It combines that with CSS media queries to show or hide an element in the document flow at different device widths.

{{< hint info >}}
**Tip:** The usage is very similar to the **Breakpoint** mixin, and it accepts the same arguments.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number (with unit)" description="Sets the width value at which your styles will be applied." >}}
  {{< arguments/row name="$mode" type="string" description="Sets the `width` media feature. Accepts the values `only`, `min`, `max`, and `between`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin and pass the width at which you want the selected element removed from the document layout.
{{< highlight scss >}}
.element{
  @include remove(500px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (width: 500px) {
  .element {
    display: none;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can **specify a range** where you don't want the selected element to appear.
{{< highlight scss >}}
.element{
  @include remove(500px, 1024px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 500px) and (max-width: 1024px) {
  .element {
    display: none;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use the `$mode` option to set the `width` media feature. It accepts the values `only`, `min`, `max`, and `between`.
{{< highlight scss >}}
.element{
  @include remove(min, 1200px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 1200px) {
  .element {
    display: none;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use the predefined breakpoint values, which are `xsmall`, `small`, `medium`, `large`, and `xlarge`.
{{< highlight scss >}}
.element{
  @include remove(max, medium);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (max-width: 768px) {
  .element {
    display: none;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can set a range by using predefined values as well!
{{< highlight scss >}}
.element{
  @include remove(small, medium);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 576px) and (max-width: 767px) {
  .element {
    display: none;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}



