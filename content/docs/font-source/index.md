---
title: "fontSource"
page_title: "fontSource Sass Function"
page_description: "Builds one src entry for an @font-face rule."
page_keywords: "Gerillass fontSource, Sass fontSource, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# fontSource

{{< function type="Function" name="fontSource" file="font-source" >}}
Builds one src entry for an @font-face rule.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$font-family" type="string" description="Accepts the family name." >}}
  {{< arguments/row name="$file-path" type="string" description="Accepts path without an extension." >}}
  {{< arguments/row name="$file-formats" type="string" description="Accepts one of eot, woff2, woff, ttf, svg." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  content: "#{fontSource("Inter", "/fonts/inter", woff2)}";
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  content: 'url("/fonts/inter.woff2") format("woff2")';
}
{{< /highlight >}}
{{< /highlightwrap >}}
