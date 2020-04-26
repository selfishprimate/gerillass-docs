# Radial Gradient

{{< featured type="Mixin" name="radial-gradient" >}}
This mixin helps you to generate radial gradients easily.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="**Important:** When you use the color-stop points together with the color values, each group of values must be wrapped with parentheses and separated by space. For more see the <a href='#examples'>examples</a>.">}}
    {{< arguments/row name="$shape" type="string" description="This option sets the shape of the gradient. Accepts `circle` or `ellipse` values. The default value is set to `ellipse`. To skip this argument use `null`." >}}
    {{< arguments/row name="$position" type="string, number" description="Sets the position of the gradient's shape. Accepts the following values: `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left`, `center`, `closest-side`, `farthest-side`, `closest-corner`, `farthest-corner`." >}}
    {{< arguments/row name="$colors" type="list" description="Accepts a list of colors with or without the color-stop points. You can pass as many color values ​​as you want." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Let's call the mixin and pass some values by using the one-line method.
{{< highlight scss >}}
.element{
    @include gls-radial-gradient(circle, center, red orange);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: radial-gradient(circle at center, red, orange);
}
{{< /highlight >}}
<div class="sandbox large" style="background: radial-gradient(circle at center, red, orange);"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's change the shape of the gradient.
{{< highlight scss >}}
.element{
    @include gls-radial-gradient(ellipse, center, red orange);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: radial-gradient(ellipse at center, red, orange);
}
{{< /highlight >}}
<div class="sandbox large" style="background: radial-gradient(ellipse at center, red, orange);"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now change the position of the gradient's shape.
{{< highlight scss >}}
.element{
    @include gls-radial-gradient(circle, top-right, red orange gold);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: radial-gradient(circle at top right, red, orange, gold);
}
{{< /highlight >}}
<div class="sandbox large" style="background: radial-gradient(circle at top right, red, orange, gold);"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Use color-stops to make sharp transitions between the colors.
{{< highlight scss >}}
.element{
    @include gls-radial-gradient(circle, center, (darkslateblue 0 10%) (white 10% 20%) (DodgerBlue 20% 30%) (PowderBlue 30% 100%));
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: radial-gradient(circle at center, darkslateblue 0 10%, white 10% 20%, dodgerblue 20% 30%, powderblue 30% 100%);
}
{{< /highlight >}}
<div class="sandbox large" style="background: radial-gradient(circle at center, darkslateblue 0 10%, white 10% 20%, dodgerblue 20% 30%, powderblue 30% 100%);"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try it with the named arguments.
{{< hint info >}}
To use **named arguments** may be time-consuming compared to using **ordinal arguments** but it is definitely easier to use, especially if the number of arguments that you have to pass is too many.
{{< /hint >}}
{{< highlight scss >}}
.element{
    @include gls-radial-gradient(
        $shape: circle,
        $position: top,
        $colors: pink crimson
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: radial-gradient(circle at top, pink, crimson);
}
{{< /highlight >}}
<div class="sandbox large" style="background: radial-gradient(circle at top, pink, crimson);"></div>
{{< /highlightwrap >}}

## Related Links
* [Radial Gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/radial-gradient)