---
title: "Is Number"
page_title: "Is Number Sass Function"
page_description: "Returns the value if it is a number."
page_keywords: "Gerillass isNumber, Sass isNumber, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# Is Number

{{< function type="Function" name="isNumber" file="is-number" >}}
Returns the value if it is a number.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="value" description="Accepts any value." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Validating a numeric argument in a mixin of your own.
{{< highlight scss >}}
@mixin z($layer) {
  position: relative;
  z-index: isNumber($layer);
}
.modal {
  @include z(100);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.modal {
  position: relative;
  z-index: 100;
}
{{< /highlight >}}
{{< /highlightwrap >}}
