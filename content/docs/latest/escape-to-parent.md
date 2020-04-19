# Escape to Parent

{{< featured type="Mixin" name="escape-to-parent" >}}
This mixin allows you to **escape to the parent** element and use multiple class or id selectors with it. Therefore you can easily control how the selected child element(s) appear differently on various devices.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="Note that you have to use quoted string!">}}
    {{< arguments/row name="$selector" type="string (quoted)" description="Acceps a value as a `class` or `id` selector." >}}
{{< /arguments/table >}}

## Examples

{{< highlight-wrapper class="example">}}
Call the mixin as many as the number of cases that you want the element response to and pass the related argument for each.
{{< highlight scss >}}
.element-container{
    .element{
        @include escape-to-parent(".smartphone"){
            background-color: red;
        }
        @include escape-to-parent(".tablet"){
            background-color: blue;
        }
        @include escape-to-parent(".desktop"){
            background-color: green;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.smartphone.element-container .element {
    background-color: red;
}
.tablet.element-container .element {
    background-color: blue;
}
.desktop.element-container .element {
    background-color: green;
}
{{< /highlight >}}
{{< /highlight-wrapper >}}
