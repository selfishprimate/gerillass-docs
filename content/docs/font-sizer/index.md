---
title: "Font Sizer"
page_title: "Font Sizer Sass Function"
page_description: "Multiplies a size by a factor. Handy for a modular scale."
page_keywords: "Gerillass fontSizer, Sass fontSizer, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# Font Sizer

{{< function type="Function" name="fontSizer" file="font-sizer" >}}
Multiplies a size by a factor. Handy for a modular scale.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$size" type="number (with unit)" description="Accepts a length." >}}
  {{< arguments/row name="$time" type="number (unitless)" description="Accepts a unitless multiplier." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
A size scaled by a factor.
{{< highlight scss >}}
.title {
  font-size: fontSizer(16px, 1.5);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.title {
  font-size: 24px;
}
{{< /highlight >}}
{{< /highlightwrap >}}
