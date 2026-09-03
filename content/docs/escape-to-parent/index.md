---
title: "Escape to Parent"
page_title: "Escape to Parent Sass Mixin"
page_description: "The Escape to Parent Sass mixin allows you to escape to the parent element and use multiple class or id selectors with it."
---

# Escape to Parent

{{< mixin type="Mixin" name="escape-to-parent" >}}
The **Escape to Parent** Sass mixin allows you to **escape to the parent** element and use multiple class or id selectors with it. This makes it easy to control how the selected child elements respond in different cases.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Note that you have to use a quoted string!">}}
    {{< arguments/row name="$selector" type="string (quoted)" description="Accepts a value as a `class` or `id` selector." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Call the mixin once for each case you want the element to respond to, and pass the matching argument each time.
{{< highlight scss >}}
.parent-element{
  .element{
    @include escape-to-parent(".smartphone"){
      background-color: red;
    }
    @include escape-to-parent(".desktop"){
      background-color: green;
    }
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.smartphone.parent-element .element {
  background-color: red;
}
.desktop.parent-element .element {
  background-color: green;
}
{{< /highlight >}}
{{< /highlightwrap >}}
