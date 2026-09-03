---
title: "Hide"
page_title: "Hide Sass Mixin"
page_description: "You can improve web accessibility by hiding elements with the Hide Sass mixin. It hides content visually on a web page while keeping it accessible to assistive technologies such as screen readers."
---

# Hide

{{< mixin type="Mixin" name="hide" >}}
The **Hide** Sass mixin allows you to improve web accessibility by hiding elements. It hides content visually on a web page while keeping it accessible to assistive technologies such as screen readers.
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$toggle" type="string" description="Accepts the values `hide` and `unhide`. The default value is `hide`. Use `unhide` to reverse the effect." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin to make the selected element and all of its children visually hidden (but still accessible to screen readers).
{{< highlight scss >}}
.element {
  @include hide;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
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
Now let's pass the `unhide` value to reverse the effect.
{{< highlight scss >}}
.element {
  @include hide(unhide);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
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



