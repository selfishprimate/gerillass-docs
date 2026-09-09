---
title: "validateScissors"
page_title: "validateScissors Sass Function"
page_description: "Normalises corner values for the scissors mixin, adding px where missing."
page_keywords: "Gerillass validateScissors, Sass validateScissors, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# validateScissors

{{< function type="Function" name="validateScissors" file="validate-scissors" >}}
Normalises corner values for the scissors mixin, adding px where missing.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number" description="Accepts one to four numbers, with or without units." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  content: "#{validateScissors(12px)}";
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  content: "12px";
}
{{< /highlight >}}
{{< /highlightwrap >}}
