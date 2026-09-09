---
title: "shade"
page_title: "shade Sass Function"
page_description: "Mixes a colour towards black by a percentage."
page_keywords: "Gerillass shade, Sass shade, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# shade

{{< function type="Function" name="shade" file="shade" >}}
Mixes a colour towards black by a percentage.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$color" type="color" description="Accepts a colour." >}}
  {{< arguments/row name="$percentage" type="number (percentage)" description="Accepts a percentage." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  color: shade(red, 20%);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  color: #cc0000;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  color: shade(notacolor, 20%);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`'notacolor' is not a color value, please replace it with a valid one.`
{{< /hint >}}
