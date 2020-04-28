# Sizer

{{< featured type="Mixin" name="sizer" >}}
Sizer mixin helps you to size elements with one statement (or two). Size elements or create square or recangle shapes very easily.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="">}}
    {{< arguments/row name="$width" type="number (with unit),<br/>string" description="Sets the width of the selected element(s)." >}}
    {{< arguments/row name="$height" type="number (with unit),<br/>string" description="Sets the height of the selected element(s). The default value is set to `$width` value." >}}
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

{{< highlightwrap class="example">}}
To assign different values ​​to the width and height properties of an element, do the following:
{{< highlight scss >}}
.element{
    @include gls-sizer(500px, 100px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    width: 500px;
    height: 100px;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can pass string values as well!
{{< highlight scss >}}
.element{
    @include gls-sizer(400px, auto);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    width: 400px;
    height: auto;
}
{{< /highlight >}}
{{< /highlightwrap >}}

