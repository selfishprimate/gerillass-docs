---
title: "Validate Scissors"
page_title: "Validate Scissors Sass Function"
page_description: "Normalises corner values for the scissors mixin, adding px where missing."
page_keywords: "Gerillass validateScissors, Sass validateScissors, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# Validate Scissors

{{< function type="Function" name="validateScissors" file="validate-scissors" >}}
Normalises corner values for the scissors mixin, adding px where missing.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number" description="Accepts one to four numbers, with or without units." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Corner values normalised the way the scissors mixin does it internally.
{{< highlight scss >}}
.element {
  --corners: #{validateScissors(12px 0)};
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  --corners: 12px, 0px;
}
{{< /highlight >}}
{{< /highlightwrap >}}
