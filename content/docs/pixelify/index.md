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
Accepting a size with or without a unit.
{{< highlight scss >}}
.icon {
  width: pixelify(24);
  height: pixelify(24px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.icon {
  width: 24px;
  height: 24px;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
A quoted string where a number is expected.
{{< highlight scss >}}
.icon {
  width: pixelify("24");
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
``24` is not a valid $value for `pixelify`. Pass a number, with or without a unit.`
{{< /hint >}}
