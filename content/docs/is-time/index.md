---
title: "isTime"
page_title: "isTime Sass Function"
page_description: "Returns the value if it is a time in s or ms, and errors otherwise."
page_keywords: "Gerillass isTime, Sass isTime, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# isTime

{{< function type="Function" name="isTime" file="is-time" >}}
Returns the value if it is a time in s or ms, and errors otherwise.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="time" description="Accepts a duration such as 0.2s or 300ms, or 0." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Validating a duration argument in a mixin of your own.
{{< highlight scss >}}
@mixin fade($duration) {
  transition: opacity isTime($duration) ease;
}
.panel {
  @include fade(0.4s);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.panel {
  transition: opacity 0.4s ease;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
A length where a duration is expected.
{{< highlight scss >}}
.panel {
  transition-duration: isTime(400px);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`'400px' is not a valid time value. Time values must be specified in either seconds (s) or milliseconds (ms). Please try one of the following forms: '1s', '0.2s', or '3ms'`
{{< /hint >}}
