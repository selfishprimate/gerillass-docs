---
title: "Placeholder Shown"
page_title: "Placeholder Shown Sass Mixin"
page_description: "Placeholder Shown Sass mixin helps you to style input or textarea element that is currently displaying placeholder text by using :placeholder-shown CSS pseudo-class."
---

# Placeholder Shown

{{< mixin type="Mixin" name="placeholder-shown" >}}
**Placeholder Shown Sass mixin** helps you to style `<input>` or `<textarea>` element that is currently displaying placeholder text. As soon as the placeholder text disappears (that is, when the user starts typing), the applied style rules will also go away.
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
When you call the mixin at the root of your stylesheet it will target all the `<input>` and `<textarea>` elements.
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