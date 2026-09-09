---
title: "fillNulls"
page_title: "fillNulls Sass Function"
page_description: "Replaces null entries in a list with 0, or drops them."
page_keywords: "Gerillass fillNulls, Sass fillNulls, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# fillNulls

{{< function type="Function" name="fillNulls" file="fill-nulls" >}}
Replaces null entries in a list with 0, or drops them.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="list" description="Accepts a list that may contain nulls." >}}
  {{< arguments/row name="$seperation (comma)" type="string" description="Accepts comma, or space." >}}
  {{< arguments/row name="$skip (false)" type="boolean" description="Accepts true to leave nulls in place instead of using 0." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  margin: fillNulls(1px null 3px null, space);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  margin: 1px 0 3px 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  --x: #{fillNulls(1px null, nonsense)};
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`nonsense` is not a valid $seperation for `fillNulls`. Pass `comma`, `space` or `slash`.
{{< /hint >}}
