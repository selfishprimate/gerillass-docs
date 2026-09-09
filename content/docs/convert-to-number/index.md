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
A numeric string turned into a number you can do arithmetic with.
{{< highlight scss >}}
.column {
  width: convertToNumber("50") * 1%;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.column {
  width: 50%;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
A number that is already a number. The function parses strings.
{{< highlight scss >}}
.column {
  width: convertToNumber(50) * 1%;
}
{{< /highlight >}}
{{< highlight text >}}
Error: `50` is not a valid $value for `convertToNumber`. Pass a string made only of digits, such as `"42"`.
{{< /highlight >}}
{{< /highlightwrap >}}
