---
title: "convertToNumber"
page_title: "convertToNumber Sass Function"
page_description: "Parses a string of digits into a number."
page_keywords: "Gerillass convertToNumber, Sass convertToNumber, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# convertToNumber

{{< function type="Function" name="convertToNumber" file="convert-to-number" >}}
Parses a string of digits into a number.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="string" description="Accepts a string containing only digits." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  z-index: convertToNumber("42");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  z-index: 42;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  --x: #{convertToNumber(42)};
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`42` is not a valid $value for `convertToNumber`. Pass a string made only of digits, such as `"42"`.
{{< /hint >}}
