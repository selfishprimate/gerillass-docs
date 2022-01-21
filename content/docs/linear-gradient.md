---
title: "Linear Gradient"
page_title: "Linear Gradient Sass Mixin"
page_description: "Linear Gradient Sass mixin helps you to generate colorful CSS gradients, and it combines them with image and text elements. In this way, you can create beautiful page components."
---

# Linear Gradient

{{< mixin type="Mixin" name="linear-gradient" >}}

**Linear Gradient Sass mixin** helps you to generate colorful CSS gradients, and it combines them with image and text elements. In this way, you can create beautiful page components.

The one-line method makes it very easy to use. To generate a linear gradient you must pass values for gradient's angle of `$direction` and at least two color values. You can also add color-stop points (starting and ending positions of colors).

{{< hint info >}}
A color-stop points can be defined by `length` or a `percentage` units.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="**Important:** When you use the color-stop points together with the color values, each group of values must be wrapped with parentheses and separated by space. For more see the <a href='#examples'>examples</a>.">}}
  {{< arguments/row name="$direction" type="string, number" description="Sets the gradient line's direction of angle. Accepts `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left` values as a string. Or you can pass a custom value as a number followed by a `deg` unit." >}}
  {{< arguments/row name="$colors" type="list" description="Accepts a list of colors with or without the color-stop points. You can pass as many color values ​​as you want." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in a selector pass some values both for `$direction` and `$color` parameters.
{{< highlight scss >}}
.element{
  @include linear-gradient(right, #43c6ac #191654);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background: linear-gradient(to right, #43c6ac, #191654);
}
{{< /highlight >}}
<div class="sandbox large" style="background: linear-gradient(to right, #43c6ac, #191654);"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's try it with the named arguments and add one more color-stop.
{{< highlight scss >}}
.element{
  @include linear-gradient(
    $direction: right,
    $colors: #43c6ac #191654 #963d91
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background: linear-gradient(to right, #43c6ac, #191654, #963d91);
}
{{< /highlight >}}
<div class="sandbox large" style="background: linear-gradient(to right, #43c6ac, #191654, #963d91);"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
We can use the color-stop positioning to adjust the transition between the colors.
{{< highlight scss >}}
.element{
  @include linear-gradient(
    $direction: right,
    $colors: (#1a2a6c 0 10%) (#b21f1f 30% 60%) (#fdbb2d 90% 100%)
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background: linear-gradient(to right, #1a2a6c 0 10%, #b21f1f 30% 60%, #fdbb2d 90% 100%);
}
{{< /highlight >}}
<div class="sandbox large" style="background: linear-gradient(to right, #1a2a6c 0 10%, #b21f1f 30% 60%, #fdbb2d 90% 100%);"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's sharpen the transition between the color-stops.
{{< highlight scss >}}
.element{
  @include linear-gradient(
    $direction: right,
    $colors: (#1a2a6c 25%) (#b21f1f 25% 50%) (#fdbb2d 50% 75%) (orange 75% 100%)
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background: linear-gradient(to right, #1a2a6c 25%, #b21f1f 25% 50%, #fdbb2d 50% 75%, orange 75% 100%);
}
{{< /highlight >}}
<div class="sandbox large" style="background: linear-gradient(to right, #1a2a6c 25%, #b21f1f 25% 50%, #fdbb2d 50% 75%, orange 75% 100%);"></div>
{{< /highlightwrap >}}



## Related Links
* [Using CSS Gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Using_CSS_gradients)
* [Linear Gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient)