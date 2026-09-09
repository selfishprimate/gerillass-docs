---
title: "validateRatio"
page_title: "validateRatio Sass Function"
page_description: "Turns an aspect ratio into a value for the CSS aspect-ratio property."
page_keywords: "Gerillass validateRatio, Sass validateRatio, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# validateRatio

{{< function type="Function" name="validateRatio" file="validate-ratio" >}}
Turns an aspect ratio into a value for the CSS aspect-ratio property.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$ratio" type="string | number (unitless)" description="Accepts a string such as \"16/9\" or \"16:9\", a unitless number, or null for the 16/9 default." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  aspect-ratio: validateRatio("16/9");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  aspect-ratio: 16 / 9;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  aspect-ratio: validateRatio(1.5);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  aspect-ratio: 1.5;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  aspect-ratio: validateRatio(16 9);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`16 9` is not a valid ratio. Pass a string like `"16/9"` or `"16:9"`, a unitless number like `1.77`, or no argument at all for the 16/9 default. You passed a list.
{{< /hint >}}
