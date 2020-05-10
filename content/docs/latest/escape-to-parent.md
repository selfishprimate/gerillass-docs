---
title: "Escape to Parent"
---

# Escape to Parent

{{< mixin type="Mixin" name="escape-to-parent" >}}
**Escape to Parent** Sass mixin allows you to **escape to the parent** element and use multiple class or id selectors with it. Therefore you can easily control how the selected child element(s) response differently on various cases.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Note that you have to use quoted string!">}}
    {{< arguments/row name="$selector" type="string (quoted)" description="Acceps a value as a `class` or `id` selector." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Call the mixin as many as the number of cases that you want the element response to and pass the related argument for each.
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
