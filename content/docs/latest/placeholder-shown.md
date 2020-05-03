---
title: "Placeholder Shown"
---

# Placeholder Shown

{{< featured type="Mixin" name="placeholder-shown" >}}
This mixin helps you to style `<input>` or `<textarea>` element that is currently displaying placeholder text. 
As soon as the placeholder text disappears (that is, when the user starts typing), the style rules applied to the selected element(s) will also go away.
{{< /featured >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin and write your style rules.
{{< highlight scss >}}
input{
    @include gls-placeholder-shown{
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
@include gls-placeholder-shown{
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