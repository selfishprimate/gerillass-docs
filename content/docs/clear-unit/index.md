---
title: "clearUnit"
page_title: "clearUnit Sass Function"
page_description: "Strips the unit off a number, returning it unitless."
page_keywords: "Gerillass clearUnit, Sass clearUnit, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# clearUnit

{{< function type="Function" name="clearUnit" file="clear-unit" >}}
Strips the unit off a number, returning it unitless.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number" description="Accepts any number with a unit." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
A unitless line-height computed from two pixel sizes.
{{< highlight scss >}}
@use "sass:math";
.title {
  font-size: 24px;
  line-height: math.div(clearUnit(36px), clearUnit(24px));
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.title {
  font-size: 24px;
  line-height: 1.5;
}
{{< /highlight >}}
{{< /highlightwrap >}}
