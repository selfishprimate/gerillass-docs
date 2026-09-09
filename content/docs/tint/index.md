---
title: "tint"
page_title: "tint Sass Function"
page_description: "Mixes a colour towards white by a percentage."
page_keywords: "Gerillass tint, Sass tint, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# tint

{{< function type="Function" name="tint" file="tint" >}}
Mixes a colour towards white by a percentage.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$color" type="color" description="Accepts a colour." >}}
  {{< arguments/row name="$percentage" type="number (percentage)" description="Accepts a percentage." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
A pale background derived from the same brand colour.
{{< highlight scss >}}
$brand: crimson;
.notice {
  border: 1px solid $brand;
  background-color: tint($brand, 80%);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.notice {
  border: 1px solid crimson;
  background-color: #f8d0d8;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
The dollar sign left off a variable.
{{< highlight scss >}}
$brand: crimson;
.notice {
  background-color: tint(brand, 85%);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`'brand' is not a color value, please replace it with a valid one.`
{{< /hint >}}
