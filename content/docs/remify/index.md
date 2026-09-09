---
title: "remify"
page_title: "remify Sass Function"
page_description: "The Remify Sass function is a handy SCSS function that helps you convert pixel values to rem."
page_keywords: "Rem Sass Function, Sass pixel to rem, pixel to rem with Sass, SCSS pixel to rem, pixel to rem, How to convert pixel to rem, CSS rem unit, Sass, SCSS, Sass Library, Sass Libraries"
---

# remify

{{< function type="Function" name="remify" >}}
The **Remify Sass function** is a handy tool that helps you convert `pixel` values to `rem`. 
{{< hint info >}}
**Tip:** It is especially useful when you work with rem units and have a hard time calculating how many rems a pixel value comes to.
{{< /hint >}}
{{< hint warning >}}
**Changed in Gerillass 2.0.0:** this function used to be called `__remify`. The `__` prefix has been dropped from every utility function. Note that the old name does not raise an error, because Sass passes an unknown function through as literal CSS, so check your stylesheets for any `__` names left over.
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
  font-size: remify(30px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  font-size: 1.875rem;
}
{{< /highlight >}}
{{< /highlightwrap >}}
