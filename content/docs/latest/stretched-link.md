---
title: "Stretched Link"
---

# Stretched Link

{{< mixin type="Mixin" name="stretched-link" >}}
Suppose you have a containing element and a link inside of it. You want entire surface of this containing block to be clickable with this link. How can you do that?

**Stretched Link** Sass mixin helps you to achieve that. It spreads the clickability of a link to the entire area of its containing block. 

**Important:** Note that the containing block must have `position: relative;` style rule and the mixin must be applied to only one of its children.

{{< hint info >}}  
It can be useful when you use this mixin with HTML radio buttons or a checkbox list design patterns to control the clickability of a `<label>` element.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Sometimes there is a need to use both ::before and ::after pseudo-elements of a link. That is why the mixin provides a flexibility to choose where to apply the stretched link style rules.">}}
    {{< arguments/row name="$value" type="string" description="Accepts `before` and `after` values. If not passed default is targeting the `::before` pseudo-element of a selected element(s)." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
If no value is passed, the `::before` pseudo-element is targeted by default.
{{< highlight scss >}}
.element{
    @include gls-stretched-link;
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
Pass one of the `before` or `after` options as an argument to choose which pseudo-element that you want to target. 
{{< highlight scss >}}
.element{
    @include gls-stretched-link(after);
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
Targeting the both `::before` and `::after` pseudo-elements of a selected element(s).
{{< highlight scss >}}
.element{
    @include gls-stretched-link(before);
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
Don't forget that the containing block must have `position: relative;` style rule.

{{< highlight html >}}
<div class="containing-element">
    <a class="element" href="https://sample-site.com/">Stretched Link</a>
</div>
{{< /highlight >}}

{{< highlight scss >}}
.containing-element{
    position: relative;
    .element{
        @include gls-stretched-link(after);
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