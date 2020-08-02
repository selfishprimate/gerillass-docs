---
title: "After"
---

# After

{{< mixin type="Mixin" name="after" >}}

**After** Sass mixin helps you to generate some content or a style element after the actual content of a selected element(s).

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="When you want to fetch a given value by using custom property the name of the property must start with 'data-' prefix. For more please see the examples.">}}
  {{< arguments/row name="$content" type="string" description="You can pass a content as a string or fetch the given value using custom property like `data-content`." >}}
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
// CSS Output
.element::after {
  content: "Text to use!";
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can only target the `::after` pseudo-element and then pass a decleration block.
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
// CSS Output
.element::after {
  content: "Easy to use!";
  font-style: italic;
  color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can fetch a given value by using custom property. One thing important to remember here is the name of the property must start with 'data-' prefix.
{{< highlight html>}}
<div class="element" data-currency="TL">200</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include after("data-currency");
}
{{< /highlight >}}
{{< highlight css >}}
// CSS Output
.element::after {
  content: attr(data-currency);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can pass a value for CSS content property as a string and a decleration block between the opening and closing curly braces.
{{< highlight scss >}}
.element{
  @include after("data-currency"){
    font-size: .8em;
    color: red;
  };
}
{{< /highlight >}}
{{< highlight css >}}
// CSS Output
.element::after {
  content: attr(data-currency);
  font-size: .8em;
  color: red;
}
{{< /highlight >}}
{{< /highlightwrap >}}


