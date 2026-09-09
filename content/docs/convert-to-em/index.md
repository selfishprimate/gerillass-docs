---
title: "Convert To Em"
page_title: "Convert To Em Sass Function"
page_description: "Converts a pixel length to em, against a 16px base."
page_keywords: "Gerillass convertToEm, Sass convertToEm, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# Convert To Em

{{< function type="Function" name="convertToEm" file="convert-to-em" >}}
Converts a pixel length to em, against a 16px base.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number (with unit)" description="Accepts a pixel length." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Spacing written in px, emitted in em.
{{< highlight scss >}}
.card {
  padding: convertToEm(24px);
  border-radius: convertToEm(8px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.card {
  padding: 1.5em;
  border-radius: 0.5em;
}
{{< /highlight >}}
{{< /highlightwrap >}}
