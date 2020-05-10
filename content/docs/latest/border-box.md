---
title: "Border Box"
---

# Border Box

{{< mixin type="Mixin" name="border-box" >}}
**Border Box** Sass mixin sets the `box-sizing` property value to `border-box` for selected HTML element(s).
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Please check out the links at the end of the page to learn more about Box Sizing">}}
    {{< arguments/row name="$value" type="string" description="Accepts `only` value. It is used only when it wants to be applied for one specific HTML element." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
If you call the mixin in a selector with no value passed the style rules will be applied to this very element and all the children in it.
{{< highlight scss >}}
.element {
    @include gls-border-box;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element, 
.element::before, 
.element::after,
.element *,
.element *::before,
.element *::after {
    box-sizing: border-box;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Pass the `only` value as an argument to apply the style rules to only one specific HTML element.
{{< highlight scss >}}
.element {
    @include gls-border-box("only");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element, 
.element::before, 
.element::after {
    box-sizing: border-box;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Call the mixin at the root of your stylesheet to target all the HTML elements.
{{< highlight scss >}}
@include gls-border-box;
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
*,
*::before,
*::after {
    box-sizing: border-box;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Articles
* [CSS Box Sizing](https://www.w3schools.com/css/css3_box-sizing.asp)
* [Box Sizing](https://css-tricks.com/box-sizing/)
