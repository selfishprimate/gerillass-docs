---
title: "Background Dots"
page_title: "Background Dots Sass Mixin"
page_description: "The Background Dots Sass mixin allows you to create stylish, colorful dotted background patterns (also known as polka dots)."
page_keywords: "CSS Dotted Background Generator, CSS Background Dots, CSS Polka Dots, CSS Dotted Gradient, CSS Background Pattern, CSS Dotted Background Pattern, CSS Multiple Dots, CSS Dots, CSS Polka Dot Background, Dot Pattern CSS, Dot Pattern Art"
---

# Background Dots

{{< mixin type="Mixin" name="background-dots" >}}
The **Background Dots** Sass mixin allows you to easily create a stylish dotted background pattern (also known as **polka dots**).
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Using two separate color values together is only possible when the `$diagonal` option is true. See the examples for more.">}}
  {{< arguments/row name="$color" type="list" description="The color or colors of the dots. Accepts no more than two color values. By default there is only one color, a translucent black." >}}
  {{< arguments/row name="$size (1em)" type="number (with unit)" description="The size of the dots. The default value is `1em`." >}}
  {{< arguments/row name="$gutter ($size * 5)" type="number (with unit)" description="The size of the space between the dots. The default value is `$size * 5`, which means `5em`." >}}
  {{< arguments/row name="$diagonal (true)" type="boolean" description="This option lets you set the line order of the dots. The default value is `true`." >}}
  {{< arguments/row name="$image" type="string (quoted)" description="Accepts the URL of an image. This option helps you add an image underneath the dots to create more stylish design elements." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments.
{{< highlight scss >}}
.element{
  @include background-dots;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background-image: 
    radial-gradient(rgba(0, 0, 0, 0.1) 1em, transparent 0), 
    radial-gradient(rgba(0, 0, 0, 0.1) 1em, transparent 0);
  background-position: 2.5em 2.5em, 10em 10em;
  background-size: 5em 5em;
  background-repeat: repeat;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-image: radial-gradient(rgba(0, 0, 0, 0.1) 1em, transparent 0), radial-gradient(rgba(0, 0, 0, 0.1) 1em, transparent 0);background-position: 2.5em 2.5em, 10em 10em;background-size: 5em 5em;background-repeat: repeat;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's play with the `$color` and `$size` arguments.
{{< highlight scss >}}
.element{
  @include background-dots(
    $color: pink,
    $size: 10px
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background-image:
    radial-gradient(pink 10px, transparent 0), 
    radial-gradient(pink 10px, transparent 0);
  background-position: 25px 25px, 100px 100px;
  background-size: 50px 50px;
  background-repeat: repeat;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-image:radial-gradient(pink 10px, transparent 0), radial-gradient(pink 10px, transparent 0);
background-position: 25px 25px, 100px 100px;background-size: 50px 50px;background-repeat: repeat;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can increase or decrease the space between the dots. Compare the result with example 2.
{{< highlight scss >}}
.element{
  @include background-dots(
    $color: pink,
    $size: 10px,
    $gutter: 70px
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background-image: 
    radial-gradient(pink 10px, transparent 0), 
    radial-gradient(pink 10px, transparent 0);
  background-position: 35px 35px, 140px 140px;
  background-size: 70px 70px;
  background-repeat: repeat;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-image: radial-gradient(pink 10px, transparent 0), radial-gradient(pink 10px, transparent 0);background-position: 35px 35px, 140px 140px;background-size: 70px 70px;background-repeat: repeat;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can add a second color value as well. Note that the second color only works when the `$diagonal` argument is `true`, and the two colors must be separated by a space.
{{< highlight scss >}}
.element{
  @include background-dots(
    $color: red orange,
    $size: 10px
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background-image: 
    radial-gradient(red 10px, transparent 0), 
    radial-gradient(orange 10px, transparent 0);
  background-position: 25px 25px, 100px 100px;
  background-size: 50px 50px;
  background-repeat: repeat;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-image: radial-gradient(red 10px, transparent 0), radial-gradient(orange 10px, transparent 0);background-position: 25px 25px, 100px 100px;background-size: 50px 50px;
background-repeat: repeat;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Set the `$diagonal` argument to `false` to make the dots look more linear.
{{< highlight scss >}}
.element{
  @include background-dots(
    $color: red,
    $size: 4px,
    $diagonal: false
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background-image: radial-gradient(red 4px, transparent 0);
  background-position: 10px 10px;
  background-size: 20px 20px;
  background-repeat: repeat;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-image: radial-gradient(red 4px, transparent 0);background-position: 10px 10px;background-size: 20px 20px;background-repeat: repeat;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's add an image and see how sexy this design piece will look!
{{< highlight scss >}}
.element{
  @include background-dots(
    $color: rgba(black, 0.1) rgba(green, 0.2),
    $size: 4px,
    $gutter: 20px,
    $image: "/images/backgrounds/03.jpg"
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background-image: 
    radial-gradient(rgba(0, 0, 0, 0.1) 4px, transparent 0), 
    radial-gradient(rgba(0, 128, 0, 0.2) 4px, transparent 0);
  background-position: 10px 10px, 40px 40px;
  background-size: 20px 20px;
  background-repeat: repeat;
  position: relative;
}
.element::before {
  content: "";
  display: block;
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-image: url("/images/backgrounds/03.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  z-index: -1;
}
{{< /highlight >}}
<style>
.example06::before{
  content: "";
  display: block;
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-image: url("/images/backgrounds/03.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  z-index: -1;
}
</style>
<div class="sandbox xxlarge example06" style="border-radius:3px; overflow: hidden; background-image: radial-gradient(rgba(0, 0, 0, 0.1) 4px, transparent 0), radial-gradient(rgba(0, 128, 0, 0.2) 4px, transparent 0);background-position: 10px 10px, 40px 40px;background-size: 20px 20px;background-repeat: repeat;position: relative;"></div>
{{< /highlightwrap >}}


