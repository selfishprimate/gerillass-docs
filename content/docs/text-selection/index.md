---
title: "Text Selection"
page_title: "Text Selection Sass Mixin"
page_description: "The Text Selection Sass mixin helps you style the portion of text (or an element) that a user has selected."
---

# Text Selection

{{< mixin type="Mixin" name="text-selection" >}}
The **Text Selection** Sass mixin helps you style the portion of text (or an element) that a user has selected.
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="string" description="Accepts the `only` value. Use it when you want to apply the styles to one specific HTML element." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
If you call it inside a selector without passing a value, the style rules apply to that element and its children.
{{< highlight scss >}}
.element{
  @include text-selection{
    color: pink;
    background-color: red;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::selection,
.element *::selection {
  color: pink;
  background-color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Pass the `only` value as an argument to apply the style rules to only one specific HTML element.
{{< highlight scss >}}
.element{
  @include text-selection(only){
    color: pink;
    background-color: red;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::selection {
  color: pink;
  background-color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Call the mixin at the root of your stylesheet to target all the HTML elements.
{{< highlight scss >}}
@include text-selection{
  color: pink;
  background-color: red;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
::selection {
  color: pink;
  background-color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}