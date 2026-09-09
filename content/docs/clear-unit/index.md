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
{{< highlight scss >}}
.element {
  line-height: clearUnit(24px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  line-height: 24;
}
{{< /highlight >}}
{{< /highlightwrap >}}
