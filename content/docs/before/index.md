---
title: "Before"
page_title: "Before Sass Mixin"
page_description: "The Before Sass mixin is an easy way to use the ::before CSS pseudo-element. You can insert text or design elements before the content of each selected element."
page_keywords: "CSS After Before, CSS Before Icon, CSS Before Usage, CSS Pseudo Classes, CSS Before Selector"
---

# Before

{{< mixin type="Mixin" name="before" >}}
The **Before** Sass mixin helps you generate content or a style element before the actual content of the selected element or elements.
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
  @include before("Text to use!");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::before {
  content: "Text to use!";
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can target the `::before` pseudo-element on its own and pass a declaration block.
{{< highlight scss >}}
.element{
  @include before{
    content: "Easy to use!";
    font-style: italic;
    color: red;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::before {
  content: "Easy to use!";
  font-style: italic;
  color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
You can fetch a value using a custom property. One important thing to remember is that the name of the property must start with the 'data-' prefix.
{{< highlight html>}}
<div class="element" data-currency="$">200</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include before("data-currency");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::before {
  content: attr(data-currency);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can pass a value for the CSS content property as a string, and a declaration block between the opening and closing curly braces.
{{< highlight scss >}}
.element{
  @include before("data-currency"){
    font-size: .8em;
    color: red;
  };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::before {
  content: attr(data-currency);
  font-size: .8em;
  color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}


