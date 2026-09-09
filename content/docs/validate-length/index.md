---
title: "validateLength"
page_title: "validateLength Sass Function"
page_description: "Returns the value if it is a length or one of auto, inherit, initial, 0."
page_keywords: "Gerillass validateLength, Sass validateLength, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# validateLength

{{< function type="Function" name="validateLength" file="validate-length" >}}
Returns the value if it is a length or one of auto, inherit, initial, 0.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number (with unit)" description="Accepts a length with a unit, or auto, inherit, initial, 0." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  width: validateLength(20px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  width: 20px;
}
{{< /highlight >}}
{{< /highlightwrap >}}
