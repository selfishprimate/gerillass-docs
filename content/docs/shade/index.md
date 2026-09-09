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
A darker hover state derived from one brand colour.
{{< highlight scss >}}
$brand: crimson;
.button {
  background-color: $brand;
}
.button:hover {
  background-color: shade($brand, 20%);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.button {
  background-color: crimson;
}

.button:hover {
  background-color: #b01030;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
The dollar sign left off a variable.
{{< highlight scss >}}
$brand: crimson;
.button:hover {
  background-color: shade(brand, 20%);
}
{{< /highlight >}}
{{< highlight text >}}
Error: 'brand' is not a color value, please replace it with a valid one.
{{< /highlight >}}
{{< /highlightwrap >}}
