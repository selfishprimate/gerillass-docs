---
title: "Text Gradient"
page_title: "Text Gradient Sass Mixin"
page_description: "The Text Gradient Sass mixin (also known as CSS Gradient Text) helps you add a gradient overlay to a text element. It provides a one-line method to set the direction of the gradient line, the color values, and the color stop positions very easily."
page_keywords: "Text Gradient, CSS Text Gradient, Sass Text Gradient, Text Gradient Generator, CSS Text Gradient Left to Right, CSS Text Gradient Overlay, CSS Text Gradient Top to Bottom, CSS Give Text Gradient Color, Tailwind CSS Text Gradient"
---

# Text Gradient

{{< mixin type="Mixin" name="text-gradient" >}}

The **Text Gradient** Sass mixin (also known as **CSS Gradient Text**) helps you add a gradient overlay to a text element. It provides a one-line method to set the direction of the gradient line, the color values, and the color stop positions very easily. 

{{< hint info >}}
A color stop position can be defined with `length` or `percentage` units.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="**Important:** When you use color stop points together with the color values, each group of values must be wrapped in parentheses and separated by a space. See the <a href='#examples'>examples</a> for more.">}}
  {{< arguments/row name="$direction" type="string, number" description="Sets the direction of the gradient line. Accepts the string values `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, and `top-left`. You can also pass a custom value as a number followed by a `deg` unit." >}}
  {{< arguments/row name="$colors" type="list" description="Accepts a list of colors, with or without color stop points. You can pass as many color values as you want." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
First, let's forget about color stop positioning and pass values only for the `$direction` and `$colors` arguments. 
{{< highlight scss >}}
.element{
  @include text-gradient(right, orange red purple blue green);
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
The one-line method (also known as using **positional arguments**) can be confusing sometimes. To explain clearly how this mixin works, let's use **named arguments** (not harder, just a little slower) to pass some values.
{{< highlight scss >}}
.element{
  @include text-gradient(
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
Now let's try it with color stop positions to make it a bit more complex.
{{< highlight scss >}}
.element{
  @include text-gradient(
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
You can use the starting position and the ending position of a color together.
{{< highlight scss >}}
.element{
  @include text-gradient(
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
The transitions between the colors do not always have to be as sharp as in the examples above.
{{< highlight scss >}}
.element{
  @include text-gradient(
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

If you want to master this, you need a clear understanding of how **linear-gradient()** works. For more, check out the links below:

## Related Links
* [Using CSS Gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Using_CSS_gradients)
* [Linear Gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient)