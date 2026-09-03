---
title: "Radial Gradient"
page_title: "Radial Gradient Sass Mixin"
page_description: "The Radial Gradient Sass mixin helps you generate beautiful radial CSS gradients. It uses the radial-gradient CSS function."
---

# Radial Gradient

{{< mixin type="Mixin" name="radial-gradient" >}}

The **Radial Gradient Sass mixin** helps you generate beautiful radial CSS gradients. It uses the radial-gradient CSS function.

The one-line method makes it very easy to use. To generate a radial gradient, you must pass values for the `$shape` and `$position` of the gradient, and for `$colors` (you need at least two color values). You can also add color stop points (the starting and ending positions of the colors).

{{< hint info >}}
Color stop points can be defined with `length` or `percentage` units.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="**Important:** When you use color stop points together with the color values, each group of values must be wrapped in parentheses and separated by a space. See the <a href='#examples'>examples</a> for more.">}}
  {{< arguments/row name="$shape" type="string" description="Sets the shape of the gradient. Accepts the values `circle` and `ellipse`. The default value is `ellipse`. To skip this argument, use `null`." >}}
  {{< arguments/row name="$position" type="string, number" description="Sets the position of the gradient's shape. Accepts the following values: `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left`, `center`, `closest-side`, `farthest-side`, `closest-corner`, `farthest-corner`." >}}
  {{< arguments/row name="$colors" type="list" description="Accepts a list of colors, with or without color stop points. You can pass as many color values as you want." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Let's call the mixin and pass some values by using the one-line method.
{{< highlight scss >}}
.element{
  @include radial-gradient(circle, center, red orange);
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
  @include radial-gradient(ellipse, center, red orange);
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
  @include radial-gradient(circle, top-right, red orange gold);
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
Use color stops to make sharp transitions between the colors.
{{< highlight scss >}}
.element{
  @include radial-gradient(circle, center, (darkslateblue 0 10%) (white 10% 20%) (dodgerblue 20% 30%) (powderblue 30% 100%));
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
Using **named arguments** may take a little longer than using **positional arguments**, but it is definitely easier, especially when you pass a lot of arguments.
{{< /hint >}}
{{< highlight scss >}}
.element{
  @include radial-gradient(
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