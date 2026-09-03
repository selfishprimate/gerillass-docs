---
title: "Antialias"
page_title: "Antialias Sass Mixin"
page_description: "The Antialias Sass mixin provides smooth font rendering. It smooths fonts at the pixel level and prevents subpixel rendering."
---

# Antialias

{{< mixin type="Mixin" name="antialias" >}}
The **Antialias** Sass mixin provides smooth font rendering. It smooths fonts at the pixel level and prevents subpixel rendering.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Please check out the links at the end of the page for more information about font smoothing.">}}
    {{< arguments/row name="$value" type="string" description="Accepts the `only` value. Use it when you want to apply the styles to one specific HTML element." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
If you call it inside a selector without passing a value, the style rules apply to that element and all of its children.
{{< highlight scss >}}
.element{
  @include antialias;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element, .element:before, .element:after,
.element *,
.element *::before,
.element *::after {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Pass the `only` value as an argument to apply the style rules to only one specific HTML element.
{{< highlight scss >}}
.element{
  @include antialias(only);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element, .element::before, .element::after {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Call the mixin at the root of your stylesheet to target all the HTML elements.
{{< highlight scss >}}
@include antialias;
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
*,
*::before,
*::after {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Articles
* [Stop Fixing Font Smoothing](https://usabilitypost.com/2012/11/05/stop-fixing-font-smoothing/)  
* [Font Smooth](https://www.zachleat.com/web/font-smooth/)