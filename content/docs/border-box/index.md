---
title: "Border Box"
page_title: "Border Box Sass Mixin"
page_description: "The Border Box Sass mixin sets the box-sizing CSS property to border-box for the selected HTML elements."
---

# Border Box

{{< mixin type="Mixin" name="border-box" >}}
The **Border Box** Sass mixin sets the [box-sizing CSS property](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) to `border-box` for the selected HTML elements. This keeps the padding and the border inside the element.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Please check out the links at the end of the page to learn more about box sizing.">}}
  {{< arguments/row name="$value" type="string" description="Accepts the `only` value. Use it when you want to apply the styles to one specific HTML element." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
If you call the mixin inside a selector without passing a value, the style rules apply to that element and all of its children.
{{< highlight scss >}}
.element {
  @include border-box;
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
Pass the `only` value as an argument to apply the style rules only to the selected element.
{{< highlight scss >}}
.element {
  @include border-box("only");
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
@include border-box;
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
