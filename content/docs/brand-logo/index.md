---
title: "Brand Logo"
page_title: "Brand Logo Sass Mixin"
page_description: "The Brand Logo Sass mixin helps you create an SEO-friendly logo component for your brand's website using CSS best practices."
---

# Brand Logo

{{< mixin type="Mixin" name="brand-logo" >}}
The **Brand Logo** Sass mixin helps you create an SEO-friendly logo component for your brand's website using CSS best practices.
{{< hint info >}}
This is a **Gerillass** technique for **image replacement**. There are other methods too. Check out the links at the end of this article to find out more.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$width" type="number (with unit)" description="Sets the width value of the logo image." >}}
  {{< arguments/row name="$height" type="number (with unit)" description="Sets the height value of the logo image." >}}
  {{< arguments/row name="$image-url" type="string" description="Sets the URL of the logo image. Works best with absolute URLs. This argument is optional, so you can also specify the image with the style attribute." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
It is important to use markup similar to the example below. The containing element does not have to be an `<h1>` tag, so feel free to change it depending on the SEO strategy you use on your site.

{{< hint info >}}
In this example, I create a logo for **Coolors**. You can use your own brand's logo file and change the logo text if you like.
{{< /hint >}}
{{< highlight html >}}
<h1 class="brand-logo">
  <a href="#">Coolors</a>
</h1>
{{< /highlight >}}

Now simply call the mixin as in the example below, and change the argument values to fit your brand logo.

{{< highlight scss >}}
.brand-logo{
  @include brand-logo(
    $width: 100px,
    $height: 30px,
    $image-url: "https://coolors.co/assets/img/logo.svg"
  );
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.brand-logo {
  position: relative;
  display: inline-block;
  width: 100px;
  height: 30px;
  background-image: url("https://coolors.co/assets/img/logo.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: 100%;
}
.brand-logo a {
  display: block;
  width: 0;
  height: 0;
  overflow: hidden;
}
.brand-logo a::after {
  content: "";
  position: absolute;
  pointer-events: auto;
  background-color: rgba(0, 0, 0, 0);
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1;
}
{{< /highlight >}}

<style>
.brand-logo.example01 {
  position: relative;
  display: inline-block;
  width: 100px;
  height: 30px;
  background-image: url("https://coolors.co/assets/img/logo.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: 100%;
  margin: 0;
}
.brand-logo.example01 a {
  display: block;
  width: 0;
  height: 0;
  overflow: hidden;
}
.brand-logo.example01 a::after {
  content: "";
  position: absolute;
  pointer-events: auto;
  background-color: rgba(0, 0, 0, 0);
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1;
}
</style>

<h1 class="brand-logo example01">
  <a href="#">Coolors</a>
</h1>

{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
As mentioned before, the `$image-url` argument is optional. With that in mind, let's specify the logo image using the selected element's style attribute.
{{< hint info >}}
Note that the `background-image` declaration has disappeared from the generated CSS.
{{< /hint >}}
{{< highlight html >}}
<h1 class="brand-logo" style="background-image: url(https://coolors.co/assets/img/logo.svg);">
  <a href="#">Coolors</a>
</h1>
{{< /highlight >}}
{{< highlight scss >}}
.brand-logo{
  @include brand-logo(
    $width: 100px,
    $height: 30px
  );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.brand-logo {
  display: inline-block;
  position: relative;
  width: 100px;
  height: 30px;
  background-position: center;
  background-repeat: no-repeat;
  background-size: 100%;
}
.brand-logo a {
  display: block;
  width: 0;
  height: 0;
  overflow: hidden;
}
.brand-logo a::after {
  content: "";
  position: absolute;
  pointer-events: auto;
  background-color: rgba(0, 0, 0, 0);
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Links
* [Nine Techniques for CSS Image Replacement](https://css-tricks.com/css-image-replacement/)
* [A History of CSS Image Replacement](https://www.sitepoint.com/css-image-replacement-text-indent-negative-margins-and-more/)


