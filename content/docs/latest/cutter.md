# Cutter

{{< featured type="Mixin" name="cutter" >}}
Sizer mixin helps you to size elements with one statement (or two). Size elements or create square or recangle shapes very easily.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="">}}
    {{< arguments/row name="$width" type="number (with unit),<br/>string" description="Sets the width of the selected element(s)." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Call the mixin to adjust the `$width` and the `$height` of an element.
{{< highlight scss >}}
.element{
    @include gls-sizer(200px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    width: 200px;
    height: 200px;
}
{{< /highlight >}}
{{< /highlightwrap >}}
