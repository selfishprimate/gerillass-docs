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
{{< highlight scss >}}
.element {
  content: clearWhitespace("a b c");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  content: "abc";
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  --x: #{clearWhitespace(42)};
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`42` is not a valid $string for `clearWhitespace`. Pass a string.
{{< /hint >}}
