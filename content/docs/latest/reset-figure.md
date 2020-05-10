---
title: "Reset Figure"
---

# Reset Figure
{{< featured type="Mixin" name="reset-figure" >}}
**Reset Figure** Sass mixin helps you to reset the margin values of `<figure>` elements to `0` and make the `<img>` element responsive (fluid) in it. 
{{< /featured >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in a selector that targets the `<figure>` element itself.
{{< highlight scss >}}
figure{
    @include gls-reset-figure;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
figure {
    margin: 0;
}
figure img {
    display: block;
    width: 100%;
}
{{< /highlight >}}
{{< /highlightwrap >}}

