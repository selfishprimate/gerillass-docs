---
title: "Remove"
page_title: "Remove Sass Mixin"
page_description: "Remove Sass mixin is to help you to set the display CSS property of an element to none, and it combines it with CSS media queries to show or hide an element in the document flow based on the various device widths."
---

# Remove

{{< mixin type="Mixin" name="remove" >}}
**Remove Sass mixin** is to help you to set the `display` CSS property of an element to `none`, and it combines it with CSS media queries to show or hide an element in the document flow based on the various device widths.

{{< hint info >}}
**Tip:** The usage is very similar to **Breakpoint** mixin. Accepts the same arguments as it is.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number (with unit)" description="Sets the width value to which your styles will be applied." >}}
  {{< arguments/row name="$mode" type="string" description="Sets the `width` media feature. Accepts `only`, `min`, `max` or `between` values." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin and pass the width value for which you want the selected element to remove from the documen layout.
{{< highlight scss >}}
.element{
  @include remove(500px);
}
{{< /highlight >}}
{{< highlight css >}}
// CSS Output
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
// CSS Output
@media (min-width: 500px) and (max-width: 1024px) {
  .element {
    display: none;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use `$mode` options to set the `width` media feature. Accepts `only`, `min`, `max` or `between` values.
{{< highlight scss >}}
.element{
  @include remove(min, 1200px);
}
{{< /highlight >}}
{{< highlight css >}}
// CSS Output
@media (min-width: 1200px) {
  .element {
    display: none;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use predefined breakpoint values which are: `xsmall`, `small`, `medium`, `large`, `xlarge`.
{{< highlight scss >}}
.element{
  @include remove(max, medium);
}
{{< /highlight >}}
{{< highlight css >}}
// CSS Output
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
// CSS Output
@media (min-width: 576px) and (max-width: 767px) {
  .element {
    display: none;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}



