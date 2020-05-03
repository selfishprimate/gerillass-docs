---
title: "Clearfix"
---

# Clearfix

{{< featured type="Mixin" name="clearfix" >}}
Clearfix mixin helps you to clear floats to prevent broken layouts and must be applied to the parent element.
{{< /featured >}}

## Examples

{{< highlightwrap class="example">}}
Simply clear floats by calling the mixin in the parent element's selector.
{{< highlight scss >}}
.element{
    @include gls-clearfix;
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

