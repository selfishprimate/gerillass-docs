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
Validating a colour argument in a mixin of your own.
{{< highlight scss >}}
@mixin badge($color) {
  background-color: isColor($color);
  color: white;
}
.badge {
  @include badge(crimson);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.badge {
  background-color: crimson;
  color: white;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
The dollar sign left off a variable, so a bare word arrives instead of a colour.
{{< highlight scss >}}
$brand: crimson;
.badge {
  background-color: isColor(brand);
}
{{< /highlight >}}
{{< highlight text >}}
Error: 'brand' is not a color value, please replace it with a valid one.
{{< /highlight >}}
{{< /highlightwrap >}}
