---
title: "After"
page_title: "After Sass Mixin"
page_description: "The After Sass mixin is an easy way to use the ::after CSS pseudo-element. You can insert text or design elements after the content of each selected element."
page_keywords: "CSS After Before, CSS After Icon, CSS After Usage, CSS Pseudo Classes, CSS After Selector"
---

# After

{{< mixin type="Mixin" name="after" >}}

The **After** Sass mixin helps you generate content or a style element after the actual content of the selected element or elements.

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="When you want to fetch a value using a custom property, the name of the property must start with the 'data-' prefix. See the examples for more.">}}
  {{< arguments/row name="$content" type="string" description="You can pass content as a string, or fetch a value using a custom property such as `data-content`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply pass a value as a string.
{{< highlight scss >}}
.element{
  @include after("Text to use!");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
  content: "Text to use!";
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can target the `::after` pseudo-element on its own and pass a declaration block.
{{< highlight scss >}}
.element{
  @include after{
    content: "Easy to use!";
    font-style: italic;
    color: red;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
  content: "Easy to use!";
  font-style: italic;
  color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can fetch a value using a custom property. One important thing to remember is that the name of the property must start with the 'data-' prefix.
{{< highlight html>}}
<div class="element" data-currency="TL">200</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include after("data-currency");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
  content: attr(data-currency);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can pass a value for the CSS content property as a string, and a declaration block between the opening and closing curly braces.
{{< highlight scss >}}
.element{
  @include after("data-currency"){
    font-size: .8em;
    color: red;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
  content: attr(data-currency);
  font-size: .8em;
  color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}


