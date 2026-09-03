---
title: "Stretched Link"
page_title: "Stretched Link Sass Mixin"
page_description: "The Stretched Link Sass mixin helps you make any HTML element clickable by stretching a nested link across its entire area."
page_keywords: "Stretched Link, Bootstrap Stretched Link, Stretched Link without Bootstrap, Tailwind Stretched Link, Stretched Link Example, CSS Stretched Link, Sass Stretched Link, SCSS Stretched Link, Stretched Link Bootstrap 5"
---

# Stretched Link

{{< mixin type="Mixin" name="stretched-link" >}}
Suppose you have a container element with a link inside it, and you want the entire surface of that container to be clickable through the link. How can you do that?

The **Stretched Link** Sass mixin helps you do that. It spreads the clickable area of a link across the entire containing block. 

**Important:** Note that the containing block must have the `position: relative;` style rule, and the mixin must be applied to only one of its children.

{{< hint info >}}  
It can be useful with HTML radio buttons or checkbox list design patterns, to control the clickable area of a `<label>` element.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Sometimes you need to use both the ::before and ::after pseudo-elements of a link. That is why the mixin lets you choose where to apply the stretched link style rules.">}}
    {{< arguments/row name="$value" type="string" description="Accepts the values `before` and `after`. If you do not pass a value, it targets the `::before` pseudo-element of the selected elements." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
If no value is passed, the `::before` pseudo-element is targeted by default.
{{< highlight scss >}}
.element{
  @include stretched-link;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::before {
  content: "";
  position: absolute;
  pointer-events: auto;
  background-color: rgba(0, 0, 0, 0);
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Pass either the `before` or the `after` option as an argument to choose which pseudo-element you want to target. 
{{< highlight scss >}}
.element{
  @include stretched-link(after);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
  content: "";
  position: absolute;
  pointer-events: auto;
  background-color: rgba(0, 0, 0, 0);
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
}
{{< /highlight >}}
{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
Targeting both the `::before` and `::after` pseudo-elements of the selected elements.
{{< highlight scss >}}
.element{
  @include stretched-link(before);
  &:after{
    content: "\2192";
  }
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.element::before {
  content: "";
  position: absolute;
  pointer-events: auto;
  background-color: rgba(0, 0, 0, 0);
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
}
.element::after {
  content: "\2192";
}
{{< /highlight >}}

{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Don't forget that the containing block must have the `position: relative;` style rule.

{{< highlight html >}}
<div class="containing-element">
  <a class="element" href="https://sample-site.com/">Stretched Link</a>
</div>
{{< /highlight >}}

{{< highlight scss >}}
.containing-element{
  position: relative;
  .element{
    @include stretched-link(after);
  }
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.containing-element {
  position: relative;
}
.containing-element .element::after {
  content: "";
  position: absolute;
  pointer-events: auto;
  background-color: rgba(0, 0, 0, 0);
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
}
{{< /highlight >}}

{{< /highlightwrap >}}