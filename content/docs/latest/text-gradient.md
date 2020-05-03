---
title: "Text Gradient"
---

# Text Gradient

{{< featured type="Mixin" name="text-gradient" >}}

Text Gradient mixin (also know as **CSS Gradient Text**) helps you to add a gradient overlay to a text element. Provides a one-line method to set the gradient line's angle of direction, color values and the color-stop positions very easily. 

{{< hint info >}}
A color-stop position can be defined by `length` or a `percentage` units.
{{< /hint >}}

{{< /featured >}}

## Arguments

{{< arguments/table footnote="**Important:** When you use the color-stop points together with the color values, each group of values must be wrapped with parentheses and separated by space. For more see the <a href='#examples'>examples</a>.">}}
    {{< arguments/row name="$direction" type="string, number" description="Sets the gradient line's direction of angle. Accepts `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left` values as a string. Or you can pass a custom value as a number followed by a `deg` unit." >}}
    {{< arguments/row name="$colors" type="list" description="Accepts a list of colors with or without the color-stop points. You can pass as many color values ​​as you want." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
First, let's forget about color-stop positioning and pass some values only for `$direction` and `$color` parameters. 
{{< highlight scss >}}
.element{
    @include gls-text-gradient(right, orange red purple blue green);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: linear-gradient(
        to right, orange, red, purple, blue, green
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
}
{{< /highlight >}}
<h2 class="sandbox text" style="background: linear-gradient(to right, orange, red, purple, blue, green);color: transparent;-webkit-background-clip: text;-webkit-text-fill-color: transparent;background-clip: text;">Text Gradient is Awesome!</h2>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
One-line method (also known as **ordinal arguments**) may be confusing sometimes. To explain how this mixin works clearly let's use **named argumens** method (not the hard way but time consuming) to pass some values.
{{< highlight scss >}}
.element{
    @include gls-text-gradient(
        $direction: top-left,
        $colors: red orange
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: linear-gradient(
        to top left, red, orange
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
}
{{< /highlight >}}
<h2 class="sandbox text" style="background: linear-gradient(to top left, red, orange);color: transparent;-webkit-background-clip: text;-webkit-text-fill-color: transparent;background-clip: text;">Text Gradient is Awesome!</h2>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try it with color-stop positions to make it a bit complex.
{{< highlight scss >}}
.element{
    @include gls-text-gradient(
        $direction: bottom,
        $colors: (red 50%) (orange 50%) 
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: linear-gradient(
        to bottom, red 50%, orange 50%
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
}
{{< /highlight >}}
<h2 class="sandbox text" style="background: linear-gradient(to bottom, red 50%, orange 50%);color: transparent;-webkit-background-clip: text;-webkit-text-fill-color: transparent;background-clip: text;">Text Gradient is Awesome!</h2>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use the `starting-position` and the `ending-positions` of a color together.
{{< highlight scss >}}
.element{
    @include gls-text-gradient(
        $direction: top,
        $colors: (green 0 40%) (blue 40% 60%) (purple 60% 100%) 
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: linear-gradient(
        to top, green 0 40%, blue 40% 60%, purple 60% 100%
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
}
{{< /highlight >}}
<h2 class="sandbox text" style="background: linear-gradient(to top, green 0 40%, blue 40% 60%, purple 60% 100%);color: transparent;-webkit-background-clip: text;-webkit-text-fill-color: transparent;background-clip: text;">Text Gradient is Awesome!</h2>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
The transitions between the colors do not always have to be that sharp like in the above examples.
{{< highlight scss >}}
.element{
    @include gls-text-gradient(
        $direction: bottom,
        $colors: (red 30%) (orange 60%) (brown 80%)
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background: linear-gradient(
        to bottom, red 30%, orange 60%, brown 80%
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
}
{{< /highlight >}}
<h2 class="sandbox text" style="background: linear-gradient(to bottom, red 30%, orange 60%, brown 80%);color: transparent;-webkit-background-clip: text;-webkit-text-fill-color: transparent;background-clip: text;">Text Gradient is Awesome!</h2>
{{< /highlightwrap >}}


If you want to master this you must have a clear understanding of how **linear-gradient()** works. For more check out the links below:

## Related Links
* [Using CSS Gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Using_CSS_gradients)
* [Linear Gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient)