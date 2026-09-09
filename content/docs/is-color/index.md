---
title: "isColor"
page_title: "isColor Sass Function"
page_description: "Returns the value if every item in it is a colour, and errors otherwise."
page_keywords: "Gerillass isColor, Sass isColor, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# isColor

{{< function type="Function" name="isColor" file="is-color" >}}
Returns the value if every item in it is a colour, and errors otherwise.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="color | list" description="Accepts a colour, or a list of colours." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  color: isColor(red);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  color: isColor(nonsense);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`'nonsense' is not a color value, please replace it with a valid one.`
{{< /hint >}}
