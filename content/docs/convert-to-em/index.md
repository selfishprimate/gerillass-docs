---
title: "convertToEm"
page_title: "convertToEm Sass Function"
page_description: "Converts a pixel length to em, against a 16px base."
page_keywords: "Gerillass convertToEm, Sass convertToEm, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# convertToEm

{{< function type="Function" name="convertToEm" file="convert-to-em" >}}
Converts a pixel length to em, against a 16px base.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number (with unit)" description="Accepts a pixel length." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  margin: convertToEm(24px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  margin: 1.5em;
}
{{< /highlight >}}
{{< /highlightwrap >}}
