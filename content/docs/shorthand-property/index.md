---
title: "shorthandProperty"
page_title: "shorthandProperty Sass Function"
page_description: "Expands one to four values into the four-value CSS shorthand order."
page_keywords: "Gerillass shorthandProperty, Sass shorthandProperty, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# shorthandProperty

{{< function type="Function" name="shorthandProperty" file="shorthand-property" >}}
Expands one to four values into the four-value CSS shorthand order.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="list" description="Accepts one to four values." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  margin: shorthandProperty(10px 20px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  margin: 10px 20px 10px 20px;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

The function checks its arguments and stops the build with a message, rather than letting a wrong value through into your CSS.

{{< highlightwrap >}}
{{< highlight scss >}}
.element {
  margin: shorthandProperty(1px 2px 3px 4px 5px);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint danger >}}
`You've passed 5 arguments. Please do not pass more than 4.`
{{< /hint >}}
