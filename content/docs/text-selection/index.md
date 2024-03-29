---
title: "Text Selection"
page_title: "Text Selection Sass Mixin"
page_description: "Text Selection Sass mixin helps you to style the portion of a text (or element) that is selected by a user."
---

# Text Selection

{{< mixin type="Mixin" name="text-selection" >}}
**Text Selection** Sass mixin helps you to style the portion of a text (or element) that is selected by a user.
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="string" description="Accepts `only` value. It is used only when it wants to be applied for one specific HTML element." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
If you call it in a selector with no value passed the style rules will be applied to this element and its children.
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