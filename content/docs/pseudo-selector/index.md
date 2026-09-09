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
One rule applied to several selectors in the same state.
{{< highlight scss >}}
#{pseudoSelector(("button", ".btn", "a"), "focus-visible")} {
  outline: 2px solid crimson;
  outline-offset: 2px;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
button:focus-visible, .btn:focus-visible, a:focus-visible {
  outline: 2px solid crimson;
  outline-offset: 2px;
}
{{< /highlight >}}
{{< /highlightwrap >}}
