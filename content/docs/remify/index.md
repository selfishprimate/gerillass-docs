---
title: "Remify"
page_title: "Remify Sass Function"
page_description: "Converts a pixel length to rem, against a 16px root."
page_keywords: "Gerillass remify, Sass remify, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# Remify

{{< function type="Function" name="remify" file="remify" >}}
Converts a pixel length to rem, against a 16px root.
{{< /function >}}

{{< hint warning >}}
**Changed in Gerillass 2.0.0:** this function used to be called `__remify`. The `__` prefix has been dropped from every utility function. The old name does not raise an error, because Sass passes an unknown function through as literal CSS, so check your stylesheets for any `__` names left over.
{{< /hint >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number (with unit)" description="Accepts a pixel length." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Pixel sizes emitted as rem.
{{< highlight scss >}}
.title {
  font-size: remify(30px);
  margin-bottom: remify(12px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.title {
  font-size: 1.875rem;
  margin-bottom: 0.75rem;
}
{{< /highlight >}}
{{< /highlightwrap >}}
