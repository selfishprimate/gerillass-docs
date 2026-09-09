---
title: "clearWhitespace"
page_title: "clearWhitespace Sass Function"
page_description: "Removes every space from a string."
page_keywords: "Gerillass clearWhitespace, Sass clearWhitespace, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# clearWhitespace

{{< function type="Function" name="clearWhitespace" file="clear-whitespace" >}}
Removes every space from a string.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$string" type="string" description="Accepts any string." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Turning a font family name into a filename.
{{< highlight scss >}}
.brand {
  font-family: "Fanwood Text", serif;
  background-image: url("/fonts/#{clearWhitespace("Fanwood Text")}.svg");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.brand {
  font-family: "Fanwood Text", serif;
  background-image: url("/fonts/FanwoodText.svg");
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
A number where a string is expected.
{{< highlight scss >}}
$size: 16;
.brand {
  background-image: url("/fonts/#{clearWhitespace($size)}.svg");
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
``16` is not a valid $string for `clearWhitespace`. Pass a string.`
{{< /hint >}}
