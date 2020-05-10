---
title: "Antialias"
---

# Antialias

{{< featured type="Mixin" name="antialias" >}}
**Antialias** Sass mixin provides smooth font rendering which means smooth the font on the level of pixel and prevents the subpixels-rendering.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="Please check out the links at the end of the page for more information about Font Smoothing.">}}
    {{< arguments/row name="$value" type="string" description="Accepts `only` value. It is used only when it wants to be applied for one specific HTML element." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
If you call it in a selector with no value passed the style rules will be applied to this very element and all its children.
{{< highlight scss >}}
.element{
    @include gls-antialias;
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
    @include gls-antialias(only);
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
@include gls-antialias;
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