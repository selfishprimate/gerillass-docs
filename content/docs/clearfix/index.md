---
title: "Clearfix"
page_title: "Clearfix Sass Mixin"
page_description: "The Clearfix Sass mixin helps you fix broken layouts caused by using the float CSS property."
page_keywords: "CSS Clearfix, Clearfix Class, Clear Float CSS, Clear CSS, Clear: Both CSS"
---

# Clearfix

{{< mixin type="Mixin" name="clearfix" >}}
The **Clearfix** Sass mixin helps you clear floats to prevent broken layouts. It must be applied to the parent element.
{{< /mixin >}}

## Examples

{{< highlightwrap class="example">}}
Simply clear floats by calling the mixin inside the parent element's selector.
{{< highlight scss >}}
.element{
  @include clearfix;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
  content: "";
  display: block;
  clear: both;
}
{{< /highlight >}}
{{< /highlightwrap >}}

