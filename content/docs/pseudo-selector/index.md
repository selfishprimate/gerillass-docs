---
title: "pseudoSelector"
page_title: "pseudoSelector Sass Function"
page_description: "Appends a pseudo-class to every selector in a list."
page_keywords: "Gerillass pseudoSelector, Sass pseudoSelector, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# pseudoSelector

{{< function type="Function" name="pseudoSelector" file="pseudo-selector" >}}
Appends a pseudo-class to every selector in a list.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$elements" type="list" description="Accepts a list of selectors." >}}
  {{< arguments/row name="$pseudo (null)" type="string" description="Accepts a pseudo-class name, without the colon." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  content: "#{pseudoSelector(("button", "a"), "hover")}";
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  content: "button:hover, a:hover";
}
{{< /highlight >}}
{{< /highlightwrap >}}
