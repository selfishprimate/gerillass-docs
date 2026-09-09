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
Shorthand where only some sides are given.
{{< highlight scss >}}
.card {
  margin: fillNulls(24px null null null, space);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.card {
  margin: 24px 0 0 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
A misspelled separator.
{{< highlight scss >}}
.card {
  margin: fillNulls(24px null, spaces);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `spaces` is not a valid $seperation for `fillNulls`. Pass `comma`, `space` or `slash`.
{{< /highlight >}}
{{< /highlightwrap >}}
