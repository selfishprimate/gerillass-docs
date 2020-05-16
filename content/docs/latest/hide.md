---
title: "Hide"
---

# Hide

{{< mixin type="Mixin" name="hide" >}}
**Hide** Sass mixin helps you to hide an element visually white still make the content to be accessible to assistive technology, e.g. screen readers.
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
    {{< arguments/row name="$toggle" type="string" description="Accepts `hide` or `unhide` values. Default value is set to `hide`. Use `unhide` to reserve the affect." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin to make the selected element and all its children visually hidden (but accessible for screen readers).
{{< highlight scss >}}
.element {
    @include gls-hide;
}
{{< /highlight >}}
{{< highlight css >}}
// CSS Output
.element {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    border: 0;
    overflow: hidden;
    clip: rect(1px, 1px, 1px, 1px);
    -webkit-clip-path: inset(100%);
    clip-path: inset(100%);
    white-space: nowrap;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's pass `unhide` value to reserve the affect.
{{< highlight scss >}}
.element {
    @include gls-hide(unhide);
}
{{< /highlight >}}
{{< highlight css >}}
// CSS Output
.element {
    position: static;
    width: auto;
    height: auto;
    overflow: visible;
    clip: auto;
    -webkit-clip-path: none;
    clip-path: none;
    white-space: inherit;
}
{{< /highlight >}}
{{< /highlightwrap >}}



