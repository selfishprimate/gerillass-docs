# Background Dots

{{< featured type="Mixin" name="background-dots" >}}
This mixin allows you to easily create a stylish dotted background pattern (also known as **polka dots**).
{{< /featured >}}

## Arguments

{{< arguments/table footnote="When the `$diagonal` is true you can pass two color values to make it look more interesting. For more see the examples.">}}
    {{< arguments/row name="$color" type="list" description="The color of the dots. This argument is required." >}}
    {{< arguments/row name="$size (1em)" type="number (with unit)" description="The size of the dots." >}}
    {{< arguments/row name="$gutter ($size * 5)" type="number (with unit)" description="The size of the space between the dots." >}}
    {{< arguments/row name="$diagonal (true)" type="boolean" description="This option allows you to set line order of the dots. Default value is true." >}}
{{< /arguments/table >}}

## Examples

{{< highlight-wrapper class="example">}}
You can simply call the mixin and pass a $color value.
{{< highlight scss >}}
.element{
    height: 200px;
    @include gls-background-dots(
        $color: red
    );
}
{{< /highlight >}}
{{< highlight css >}}
.element {
    height: 200px;
    background-image: radial-gradient(red 1em, transparent 0), radial-gradient(red 1em, transparent 0);
    background-position: 2.5em 2.5em, 10em 10em;
    background-size: 5em 5em;
    background-repeat: repeat;
}
{{< /highlight >}}
{{< /highlight-wrapper >}}

{{< highlight-wrapper class="example">}}
Change the size of the dots.
{{< highlight scss >}}
.element{
    @include gls-background-dots(
        $color: red,
        $size: 5px
    );
}
{{< /highlight >}}
{{< highlight css >}}
.element {
    background-image: radial-gradient(red 5px, transparent 0), radial-gradient(red 5px, transparent 0);
    background-position: 12.5px 12.5px, 50px 50px;
    background-size: 25px 25px;
    background-repeat: repeat;
}
{{< /highlight >}}
{{< /highlight-wrapper >}}

{{< highlight-wrapper class="example">}}
Increase or decrease the space between the dots.
{{< highlight scss "linenos=table,hl_lines=4" >}}
.element{
    @include gls-background-dots(
        $color: red,
        $size: 5px,
        $gutter: 50px
    );
}
{{< /highlight >}}
{{< highlight css "linenos=table,hl_lines=4" >}}
.element {
    background-image: radial-gradient(red 5px, transparent 0), radial-gradient(red 5px, transparent 0);
    background-position: 25px 25px, 100px 100px;
    background-size: 50px 50px;
    background-repeat: repeat;
}
{{< /highlight >}}
{{< /highlight-wrapper >}}

{{< highlight-wrapper class="example">}}
You can add the second color. Note that the second color works only when `$diagonal` is true.
{{< highlight scss >}}
.element{
    @include gls-background-dots(
        $color: red pink,
        $size: 5px
    );
}
{{< /highlight >}}
{{< highlight css >}}
.element {
    background-image: radial-gradient(red 5px, transparent 0), radial-gradient(pink 5px, transparent 0);
    background-position: 12.5px 12.5px, 50px 50px;
    background-size: 25px 25px;
    background-repeat: repeat;
}
{{< /highlight >}}
{{< /highlight-wrapper >}}


