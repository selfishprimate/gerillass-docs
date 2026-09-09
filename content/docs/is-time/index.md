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
{{< highlight scss >}}
.element {
  animation-duration: isTime(0.4s);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  animation-duration: 0.4s;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  animation-duration: isTime(400px);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`'400px' is not a valid time value. Time values must be specified in either seconds (s) or milliseconds (ms). Please try one of the following forms: '1s', '0.2s', or '3ms'`
{{< /hint >}}
