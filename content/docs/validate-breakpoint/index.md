---
title: "Validate Breakpoint"
page_title: "Validate Breakpoint Sass Function"
page_description: "Resolves a breakpoint name to its width, passing other values through."
page_keywords: "Gerillass validateBreakpoint, Sass validateBreakpoint, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# Validate Breakpoint

{{< function type="Function" name="validateBreakpoint" file="validate-breakpoint" >}}
Resolves a breakpoint name to its width, passing other values through.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="string | number" description="Accepts a key from $map-for-breakpoints, or a raw length." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
A breakpoint name used as a length.
{{< highlight scss >}}
.container {
  max-width: validateBreakpoint("large");
  margin: 0 auto;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.container {
  max-width: 992px;
  margin: 0 auto;
}
{{< /highlight >}}
{{< /highlightwrap >}}
