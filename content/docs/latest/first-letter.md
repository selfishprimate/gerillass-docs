---
title: "First Letter"
---

# First Letter

{{< mixin type="Mixin" name="first-letter" >}}
**First Letter** Sass mixin helps you to apply styles to the first letter of a text block.

{{< /mixin >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any argument. 
{{< highlight scss >}}
.element {
    @include gls-text-stroke;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    color: black;
    -webkit-text-fill-color: transparent;
    -webkit-text-stroke-color: black;
    -webkit-text-stroke-width: 1px;
}
{{< /highlight >}}
<h1 style="margin: 0;color: black;-webkit-text-fill-color: transparent;-webkit-text-stroke-color: black;-webkit-text-stroke-width: 1px;">Text Stroke is Awesome!</h1>
{{< /highlightwrap >}}
