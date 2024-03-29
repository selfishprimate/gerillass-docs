---
title: "Placeholder"
page_title: "Placeholder Sass Mixin"
page_description: "Placeholder Sass mixin will help you to style the placeholder text in an `<input>` or `<textarea>` element and generate cross-browser compatible CSS code."
---

# Placeholder

{{< mixin type="Mixin" name="placeholder" >}}
**Placeholder Sass mixin** will help you to style the **placeholder text** in an `<input>` or `<textarea>` element and generate cross-browser compatible CSS code.
{{< /mixin >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin and write your style rules.
{{< highlight scss >}}
.element{
  @include placeholder{
    color: red;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::-webkit-input-placeholder {
  color: red;
}
.element::-moz-placeholder {
  color: red;
}
.element:-ms-input-placeholder {
  color: red;
}
.element:-moz-placeholder {
  color: red;
}
.element::placeholder {
  color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
When you call the mixin at the root of your stylesheet it will target all the `<input>` and `<textarea>` elements.
{{< highlight scss >}}
@include placeholder{
  color: orange;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
::-webkit-input-placeholder {
  color: orange;
}
::-moz-placeholder {
  color: orange;
}
:-ms-input-placeholder {
  color: orange;
}
:-moz-placeholder {
  color: orange;
}
::placeholder {
  color: orange;
}
{{< /highlight >}}
{{< /highlightwrap >}}