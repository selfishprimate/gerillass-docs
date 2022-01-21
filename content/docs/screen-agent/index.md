---
title: "Screen Agent"
page_title: "Screen Agent Sass Mixin"
page_description: "Screen Agent Sass mixin helps you to target elements based on the various screen resolutions."
---

# Screen Agent

{{< mixin type="Mixin" name="screen-agent" >}}
**Screen Agent Sass mixin** helps you to target elements based on the various screen resolutions.
{{< hint info >}}
Suppose you have two types of photos loading on your site: one for the normal screens, the other one is twice in size for the retina screens. In such cases, you may want to use this mixin.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="The string values must be wrapped with the quotation signs." >}}
  {{< arguments/row name="$resolution" type="string,<br/>number (with unit)" description="Accepts only one argument and three different values which targets the screen resolution: `1x`, `2x` and `3x`. Or you can pass a custom numeric value with `dpi` and `dpcm` units." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Based on the assumption above, we can give the following example.
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


