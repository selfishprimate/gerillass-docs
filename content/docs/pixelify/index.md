---
title: "pixelify"
page_title: "pixelify Sass Function"
page_description: "Returns the value with a px unit, adding one if it is missing."
page_keywords: "Gerillass pixelify, Sass pixelify, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# pixelify

{{< function type="Function" name="pixelify" file="pixelify" >}}
Returns the value with a px unit, adding one if it is missing.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number" description="Accepts a number, with or without a unit." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  width: pixelify(24);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  width: 24px;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  --x: #{pixelify(nonsense)};
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`nonsense` is not a valid $value for `pixelify`. Pass a number, with or without a unit.
{{< /hint >}}
