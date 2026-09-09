---
title: "Shorthand Property"
page_title: "Shorthand Property Sass Function"
page_description: "Expands one to four values into the four-value CSS shorthand order."
page_keywords: "Gerillass shorthandProperty, Sass shorthandProperty, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# Shorthand Property

{{< function type="Function" name="shorthandProperty" file="shorthand-property" >}}
Expands one to four values into the four-value CSS shorthand order.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="list" description="Accepts one to four values." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
One to four values expanded to the full four-value shorthand.
{{< highlight scss >}}
.card {
  padding: shorthandProperty(16px 24px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.card {
  padding: 16px 24px 16px 24px;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
Five values. CSS shorthand takes at most four.
{{< highlight scss >}}
.card {
  padding: shorthandProperty(1px 2px 3px 4px 5px);
}
{{< /highlight >}}
{{< highlight text >}}
Error: You've passed 5 arguments. Please do not pass more than 4.
{{< /highlight >}}
{{< /highlightwrap >}}
