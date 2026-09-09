---
title: "validateBreakpoint"
page_title: "validateBreakpoint Sass Function"
page_description: "Resolves a breakpoint name to its width, passing other values through."
page_keywords: "Gerillass validateBreakpoint, Sass validateBreakpoint, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# validateBreakpoint

{{< function type="Function" name="validateBreakpoint" file="validate-breakpoint" >}}
Resolves a breakpoint name to its width, passing other values through.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="string | number" description="Accepts a key from $map-for-breakpoints, or a raw length." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  width: validateBreakpoint("medium");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  width: 768px;
}
{{< /highlight >}}
{{< /highlightwrap >}}
