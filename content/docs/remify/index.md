---
title: "Remify"
page_title: "Remify Sass Function"
page_description: "Remify Sass function is a handy SCSS function to help you convert the pixel values to rem."
page_keywords: "Rem Sass Function, Sass pixel to rem, pixel to rem with Sass, SCSS pixel to rem, pixel to rem, How to convert pixel to rem, CSS rem unit, Sass, SCSS, Sass Library, Sass Libraries"
---

# Remify

{{< function type="Function" name="remify" >}}
**Remify Sass function** is a handy tool to help you convert the `pixel` values to `rem`. 
{{< hint info >}}
**Tip:** It's especially useful when you work with rem units and having hard times to calculate how many rems that a pixel value you pass.
{{< /hint >}}
{{< /function >}}
## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number (with unit)" description="The pixel value that you want it to be converted to `rem`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the function and pass a `pixel` value to it!
{{< highlight scss >}}
.element {
  font-size: __remify(30px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  font-size: 1.875rem;
}
{{< /highlight >}}
{{< /highlightwrap >}}
