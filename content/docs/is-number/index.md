---
title: "isNumber"
page_title: "isNumber Sass Function"
page_description: "Returns the value if it is a number."
page_keywords: "Gerillass isNumber, Sass isNumber, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# isNumber

{{< function type="Function" name="isNumber" file="is-number" >}}
Returns the value if it is a number.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="value" description="Accepts any value." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  z-index: isNumber(5);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  z-index: 5;
}
{{< /highlight >}}
{{< /highlightwrap >}}
