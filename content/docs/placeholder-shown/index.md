---
title: "Placeholder Shown"
page_title: "Placeholder Shown Sass Mixin"
page_description: "The Placeholder Shown Sass mixin helps you style an input or textarea element that is currently displaying placeholder text, using the :placeholder-shown CSS pseudo-class."
---

# Placeholder Shown

{{< mixin type="Mixin" name="placeholder-shown" >}}
The **Placeholder Shown Sass mixin** helps you style an `<input>` or `<textarea>` element that is currently displaying placeholder text. As soon as the placeholder text disappears (that is, when the user starts typing), the applied style rules go away too.
{{< /mixin >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin and write your style rules.
{{< highlight scss >}}
input{
  @include placeholder-shown{
    background-color: yellow;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
input:placeholder-shown {
  background-color: yellow;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
When you call the mixin at the root of your stylesheet, it targets all the `<input>` and `<textarea>` elements.
{{< highlight scss >}}
@include placeholder-shown{
  background-color: yellow;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
:placeholder-shown {
  background-color: yellow;
}
{{< /highlight >}}
{{< /highlightwrap >}}