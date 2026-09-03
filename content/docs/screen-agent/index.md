---
title: "Screen Agent"
page_title: "Screen Agent Sass Mixin"
page_description: "The Screen Agent Sass mixin helps you target elements based on different screen resolutions."
---

# Screen Agent

{{< mixin type="Mixin" name="screen-agent" >}}
The **Screen Agent Sass mixin** helps you target elements based on different screen resolutions.
{{< hint info >}}
Suppose you have two types of photos loading on your site: one for normal screens, and another one at twice the size for retina screens. In cases like that, you may want to use this mixin.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="String values must be wrapped in quotation marks." >}}
  {{< arguments/row name="$resolution" type="string,<br/>number (with unit)" description="Accepts one argument with three possible values that target the screen resolution: `1x`, `2x`, and `3x`. You can also pass a custom numeric value with `dpi` or `dpcm` units." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Based on the case above, we can give the following example.
{{< highlight scss >}}
.element{
  background-image: url(https://sample-site.com/images/sample-image-1920x1080.jpg);
  @include screen-agent("2x"){
    background-image: url(https://sample-site.com/images/sample-image-3840x2160.jpg);
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background-image: url(https://sample-site.com/images/sample-image-1920x1080.jpg);
}
@media (min-resolution: 192dpi) {
  .element {
    background-image: url(https://sample-site.com/images/sample-image-3840x2160.jpg);
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try it with a custom value.
{{< highlight scss >}}
.element{
  background-color: green;
  @include screen-agent(192dpi){
    background-color: teal;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  background-color: green;
}
@media (min-resolution: 192dpi) {
  .element {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}


