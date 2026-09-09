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
The ratio on its own, without the aspect-ratio mixin.
{{< highlight scss >}}
.hero {
  aspect-ratio: validateRatio("16:9");
}
.avatar {
  aspect-ratio: validateRatio(1);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.hero {
  aspect-ratio: 16 / 9;
}

.avatar {
  aspect-ratio: 1;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
A space between the numbers. Use a slash or a colon inside a string.
{{< highlight scss >}}
.hero {
  aspect-ratio: validateRatio(16 9);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
``16 9` is not a valid ratio. Pass a string like `"16/9"` or `"16:9"`, a unitless number like `1.77`, or no argument at all for the 16/9 default. You passed a list.`
{{< /hint >}}
