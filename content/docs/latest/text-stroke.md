# Text Stroke

{{< featured type="Mixin" name="text-stroke" >}}
This Sass mixin helps you to add stroke to text and style it very easily.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="When your stroke color is dark try to make the fallback color the same.">}}
    {{< arguments/row name="$color" type="color" description="Changes the color of the text. Default value is transparent." >}}
    {{< arguments/row name="$stroke-color" type="color" description="Changes the stroke color of the text. Default value is black." >}}
    {{< arguments/row name="$fallback-color" type="color" description="This option is for non-supporting browsers. It will prevent text to dissapear entirely in non-supporting browsers. Default value is black." >}}
    {{< arguments/row name="$stroke-width" type="number (with unit)" description="Changes the width of the stroke. You can pass the following values as well: `thin`, `medium`, `thick`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any argument. 
{{< highlight scss >}}
.element {
    @include gls-text-stroke;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    color: black;
    -webkit-text-fill-color: transparent;
    -webkit-text-stroke-color: black;
    -webkit-text-stroke-width: 1px;
}
{{< /highlight >}}
<h1 style="margin: 0;color: black;-webkit-text-fill-color: transparent;-webkit-text-stroke-color: black;-webkit-text-stroke-width: 1px;">Text Stroke is Awesome!</h1>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You even make more sexier!
{{< highlight scss >}}
.element {
    @include gls-text-stroke(
        $color: azure,
        $stroke-color: cadetblue,
        $fallback-color: cadetblue,
        $stroke-width: 1px
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    color: cadetblue;
    -webkit-text-fill-color: azure;
    -webkit-text-stroke-color: cadetblue;
    -webkit-text-stroke-width: 1px;
}
{{< /highlight >}}
<h1 style="margin: 0;color: cadetblue;-webkit-text-fill-color: azure;-webkit-text-stroke-color: cadetblue;-webkit-text-stroke-width: 1px;">Text Stroke is Awesome!</h1>
{{< /highlightwrap >}}

