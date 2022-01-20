---
title: "Clearfix"
site_title: "Clearfix Sass Mixin"
site_description: "Clearfix Sass Mixin helps you fix the broken layouts caused by using float CSS property."
site_keywords: "CSS Clearfix, Clearfix Class, Clear Float CSS, Clear CSS, Clear: Both CSS"
---

# Clearfix

{{< mixin type="Mixin" name="clearfix" >}}
**Clearfix** Sass mixin helps you to clear floats to prevent broken layouts and must be applied to the parent element.
{{< /mixin >}}

## Examples

{{< highlightwrap class="example">}}
Simply clear floats by calling the mixin in the parent element's selector.
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

