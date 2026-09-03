---
title: "Background Image"
page_title: "Background Image Sass Mixin"
page_description: "The Background Image Sass mixin allows you to apply the background-image CSS property to the selected elements."
---

# Background Image

{{< mixin type="Mixin" name="background-image" >}}
The **Background Image** Sass mixin allows you to apply background images to the selected elements. It gives you an easy, one-line method.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Use `null` if you want to skip an argument. See [the examples](#examples) for more.">}}
  {{< arguments/row name="$image-url" type="string" description="The URL of the background image." >}}
  {{< arguments/row name="$filter-color" type="color | list" description="The color or list of colors you want to apply as a filter over the background image. **Multiple color values must be separated by a space.**" >}}
  {{< arguments/row name="$filter-direction" type="string" description="The direction of the gradient. **It only works when you pass multiple color values for the `$filter-color` argument.** Accepts the values `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, and `top-left`. The default value is `top`." >}}
{{< /arguments/table >}}


## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in a selector and pass the URL of the background image.
{{< highlight scss >}}
.element{
  @include background-image("/images/backgrounds/07.jpg");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: relative;
  background-image: url("/images/backgrounds/07.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
{{< /highlight >}}
{{< sandbox class="xlarge" >}}
position: relative;background-image: url("/images/backgrounds/07.jpg");background-position: center center;background-repeat: no-repeat;background-size: cover;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's apply a color filter to it by passing a color value for the `$filter-color` argument.
{{< highlight scss >}}
.element{
  @include background-image("/images/backgrounds/07.jpg", rgba(255, 204, 153, 0.5));
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: relative;
  background-image: linear-gradient(to top, rgba(255, 204, 153, 0.5), rgba(255, 204, 153, 0.5)), url("/images/backgrounds/07.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
{{< /highlight >}}
{{< sandbox class="xlarge" >}}
position: relative;background-image: -webkit-gradient(linear, left bottom, left top, from(rgba(255, 204, 153, 0.5)), to(rgba(255, 204, 153, 0.5))), url("/images/backgrounds/07.jpg");background-image: linear-gradient(to top, rgba(255, 204, 153, 0.5), rgba(255, 204, 153, 0.5)), url("/images/backgrounds/07.jpg");background-position: center center;background-repeat: no-repeat;background-size: cover;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's pass multiple color values for `$filter-color` to make the background image look even more interesting.
{{< hint info >}}
**Important:** Multiple color values must be separated by a space.
{{< /hint >}}
{{< highlight scss >}}
.element{
  @include background-image("/images/backgrounds/07.jpg", rgba(0, 0, 0, 0.5) rgba(40, 102, 100, 0.8));
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: relative;
  background-image: linear-gradient(to top, rgba(0, 0, 0, 0.5), rgba(40, 102, 100, 0.8)), url("/images/backgrounds/07.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
{{< /highlight >}}
{{< sandbox class="xlarge" >}}
position: relative;background-image: -webkit-gradient(linear, left bottom, left top, from(rgba(0, 0, 0, 0.5)), to(rgba(40, 102, 100, 0.8))), url("/images/backgrounds/07.jpg");background-image: linear-gradient(to top, rgba(0, 0, 0, 0.5), rgba(40, 102, 100, 0.8)), url("/images/backgrounds/07.jpg");background-position: center center;background-repeat: no-repeat;background-size: cover;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try the `$filter-direction` option. While we do, let's use sharper color transitions to see the effect clearly.
{{< hint info >}}
**Tip:** The value you pass for `$filter-direction` indicates the position of the final color stop.
{{< /hint >}}
{{< highlight scss >}}
.element{
  @include background-image("/images/backgrounds/07.jpg", rgba(0, 128, 128, 0.7) rgba(255, 192, 203, 0.8), right);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: relative;
  background-image: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8)), url("/images/backgrounds/07.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
{{< /highlight >}}
{{< sandbox class="xlarge" >}}
position: relative;background-image: -webkit-gradient(linear, left top, right top, from(rgba(0, 128, 128, 0.7)), to(rgba(255, 192, 203, 0.8))), url("/images/backgrounds/07.jpg");background-image: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8)), url("/images/backgrounds/07.jpg");background-position: center center;background-repeat: no-repeat;background-size: cover;
{{< /sandbox >}}

{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
There will be times when you want to **add a background image to an element using the style attribute**, like in the example below. **In those cases, just use `null` to skip the `$image-url` argument.**
{{< hint info >}}
**Important:** Please examine the CSS output. When you add a background image to an element using the style attribute, the CSS output is different from the others. This prevents the `background-image` declarations on both sides from overriding each other.
{{< /hint >}}
{{< highlight html >}}
<div class="element" style="background-image: url(/images/backgrounds/07.jpg)"></div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include background-image(null, rgba(teal, 0.7) rgba(pink, 0.8), right);
}
{{< /highlight >}}
{{< highlight css >}}
.element {
  position: relative;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
.element::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element > * {
  position: relative;
  z-index: 1;
}
{{< /highlight >}}
<style>
.element.example05 {
  position: relative;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
.element.example05::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: -webkit-gradient(linear, left top, right top, from(rgba(0, 128, 128, 0.7)), to(rgba(255, 192, 203, 0.8)));
  background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element.example05 > * {
  position: relative;
  z-index: 1;
}
</style>
<div class="element sandbox xxlarge example05" style="background-image: url(/images/backgrounds/07.jpg)"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You are probably wondering why those `position: relative` and `z-index: 1` style rules are applied to the direct children of the selected element. **These rules exist to prevent the color filter from covering the direct children when you add the background image to an element using the style attribute.**

Let's try it with a title placed inside the selected element to see it in action. 
{{< highlight html >}}
<div class="element" style="background-image: url(/images/backgrounds/07.jpg)">
  <h2>A beautiful title text standing over the color filter.</h2>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include background-image(null, rgba(teal, 0.7) rgba(pink, 0.8), right);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: relative;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
.element::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element > * {
  position: relative;
  z-index: 1;
}
{{< /highlight >}}

<style>
.element.example06 {
  border-radius: 5px;
  display: -webkit-box;
  display: flex;
  -webkit-box-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  align-items: center;
  position: relative;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  padding: 30px;
}
.element.example06 .title {
  color: white;
  text-align: center;
  margin: 0;
}
.element.example06::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: -webkit-gradient(linear, left top, right top, from(rgba(0, 128, 128, 0.7)), to(rgba(255, 192, 203, 0.8)));
  background: linear-gradient(to right, rgba(0, 128, 128, 0.7), rgba(255, 192, 203, 0.8));
}
.element.example06 > * {
  position: relative;
  z-index: 1;
}
</style>

<div class="element sandbox large example06" style="background-image: url(/images/backgrounds/07.jpg)">
  <h2 class="title">A beautiful title text standing over the color filter.</h2>
</div>

{{< /highlightwrap >}}





