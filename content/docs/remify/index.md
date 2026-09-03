---
title: "Remify"
page_title: "Remify Sass Function"
page_description: "The Remify Sass function is a handy SCSS function that helps you convert pixel values to rem."
page_keywords: "Rem Sass Function, Sass pixel to rem, pixel to rem with Sass, SCSS pixel to rem, pixel to rem, How to convert pixel to rem, CSS rem unit, Sass, SCSS, Sass Library, Sass Libraries"
---

# Remify

{{< function type="Function" name="remify" >}}
The **Remify Sass function** is a handy tool that helps you convert `pixel` values to `rem`. 
{{< hint info >}}
**Tip:** It is especially useful when you work with rem units and have a hard time calculating how many rems a pixel value comes to.
{{< /hint >}}
{{< /function >}}
## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="number (with unit)" description="The pixel value you want to convert to `rem`." >}}
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
