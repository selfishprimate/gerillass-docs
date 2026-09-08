---
title: "Aspect Ratio"
page_title: "Aspect Ratio Sass Mixin"
page_description: "The Aspect Ratio Sass mixin holds an element to the ratio you give it, and adds what the CSS aspect-ratio property alone leaves out. It replaces the Ratio Box and Responsive Video mixins."
page_keywords: "CSS Aspect Ratio, Sass Aspect Ratio, CSS Responsive Video, Responsive YouTube Embed, CSS Image Aspect Ratio, aspect-ratio object-fit, CSS Ratio Box, Responsive Image Ratio"
aliases:
  - /docs/ratio-box/
  - /docs/responsive-video/
---

# Aspect Ratio

{{< mixin type="Mixin" name="aspect-ratio" >}}
The **Aspect Ratio Sass mixin** holds an element to the ratio you give it. CSS has an `aspect-ratio` property of its own, and this mixin adds the three things that property leaves out.

{{< hint warning >}}
**New in Gerillass 2.0.0.** This mixin replaces **Ratio Box** and **Responsive Video**, which were byte-identical to each other and are both gone. Note that it goes on **the element itself**, not on a wrapper around it. See [Coming from Ratio Box or Responsive Video](#coming-from-ratio-box-or-responsive-video).
{{< /hint >}}

{{< hint info >}}
**Why the extra declarations?** An `<img>` given a ratio but no `object-fit` is stretched rather than cropped, and an `<iframe>` carries a 2px default border, so `width: 100%` makes it overflow its container by 4px. The mixin sets `object-fit` and `border: 0` to close both gaps.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Pass `null` as the second argument to leave `object-fit` out of the output entirely.">}}
  {{< arguments/row name="$ratio (16/9)" type="string, number" description="The ratio to hold. Accepts a slash separated string such as `16/9`, a colon separated string such as `16:9`, or a bare number, where `1.5` means 1.5 to 1. The default value is `16/9`. Anything else is refused with an error." >}}
  {{< arguments/row name="$fit (cover)" type="string" description="Sets the `object-fit` property. Accepts `fill`, `contain`, `cover`, `none`, `scale-down`, or `null` to leave `object-fit` alone. The default value is `cover`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments. **The default ratio is `16/9`**.
{{< highlight scss >}}
.element{
  @include aspect-ratio;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  display: block;
  width: 100%;
  aspect-ratio: 16 / 9;
  border: 0;
  object-fit: cover;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Apply it to an image to hold the image to a ratio. Because `object-fit` defaults to `cover`, the image is cropped to fill the box instead of being stretched.
{{< highlight html >}}
<img class="element" src="/images/backgrounds/06.jpg" alt="" />
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include aspect-ratio("16:9");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  display: block;
  width: 100%;
  aspect-ratio: 16 / 9;
  border: 0;
  object-fit: cover;
}
{{< /highlight >}}
<style>
.gls-ar-example img,
.gls-ar-example iframe {
  display: block;
  width: 100%;
  border: 0;
  border-radius: 3px;
}
.gls-ar-16-9 { aspect-ratio: 16 / 9; object-fit: cover; }
.gls-ar-1-1 { aspect-ratio: 1 / 1; object-fit: contain; background-color: #f0f0ee; }
.gls-ar-4-3 { aspect-ratio: 4 / 3; object-fit: cover; }
</style>
<div class="gls-ar-example">
  <img class="gls-ar-16-9" src="/images/backgrounds/06.jpg" alt="A 16 by 9 box holding a cropped photograph" />
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
A colon and a slash mean the same thing, so `"16:9"` and `"16/9"` give identical output. Let's change the ratio to `4/3` this time.
{{< highlight scss >}}
.element{
  @include aspect-ratio("4/3");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  display: block;
  width: 100%;
  aspect-ratio: 4 / 3;
  border: 0;
  object-fit: cover;
}
{{< /highlight >}}
<div class="gls-ar-example">
  <img class="gls-ar-4-3" src="/images/backgrounds/06.jpg" alt="A 4 by 3 box holding a cropped photograph" />
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Pass a second value to change how the content fills the box. Here the box is square and the image is contained rather than cropped, so all of it stays visible.
{{< highlight scss >}}
.element{
  @include aspect-ratio("1:1", contain);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  display: block;
  width: 100%;
  aspect-ratio: 1 / 1;
  border: 0;
  object-fit: contain;
}
{{< /highlight >}}
<div class="gls-ar-example">
  <img class="gls-ar-1-1" src="/images/backgrounds/06.jpg" alt="A square box containing the whole photograph" />
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can also pass a bare number, where `1.5` means 1.5 to 1. Passing `null` as the second argument leaves `object-fit` out of the output, which is what you want when the element has no content of its own to fit.
{{< highlight scss >}}
.element{
  @include aspect-ratio(1.5, null);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  display: block;
  width: 100%;
  aspect-ratio: 1.5;
  border: 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
For an embedded video, apply the mixin **to the `<iframe>` itself**. There is no wrapper element and no padding hack.
{{< highlight html >}}
<iframe class="element" src="https://www.youtube.com/embed/JBc6JiRlsOU" title="YouTube video player" allowfullscreen></iframe>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include aspect-ratio("16/9");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  display: block;
  width: 100%;
  aspect-ratio: 16 / 9;
  border: 0;
  object-fit: cover;
}
{{< /highlight >}}
<div class="gls-ar-example">
  <iframe class="gls-ar-16-9" src="https://www.youtube.com/embed/JBc6JiRlsOU" title="YouTube video player" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

Try resizing the browser window to see the result.
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
If you want the ratio on its own, without the rest of the mixin, the `validateRatio` function accepts the same values and returns just the ratio.
{{< highlight scss >}}
.element{
  aspect-ratio: validateRatio("16:9");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  aspect-ratio: 16 / 9;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## Coming from Ratio Box or Responsive Video

Both of those mixins held a ratio with a `padding-top` hack, a pseudo-element and an absolutely positioned child. The CSS `aspect-ratio` property made all of that unnecessary, and it left the two mixins identical to each other, so they were replaced by this single one.

The rename itself is mechanical. What is not mechanical is **where the mixin goes**: the old mixins were applied to a wrapping element, and this one goes on the element itself.

{{< highlight scss >}}
// Before, on a wrapper
.hero  { @include ratio-box("16/9"); }
.video { @include responsive-video("16/9"); }

// After, on the element
.hero  { @include aspect-ratio("16/9"); }
.video iframe { @include aspect-ratio("16/9"); }
{{< /highlight >}}

{{< hint danger >}}
**This part is easy to get wrong.** A ratio on a **wrapper** does not size an `<iframe>` inside it. The iframe keeps its intrinsic 300 by 150. Measured in a browser at a container width of 640px, a ratio on the wrapper gives a 640 by 360 wrapper with a 304 by 154 iframe inside it, while a ratio on the iframe itself gives 640 by 360 with no wrapper needed.
{{< /hint >}}

If you have a wrapper `<div>` around a video embed only to hold its ratio, remove the wrapper along with the old mixin.

## Related Links
* [aspect-ratio](https://developer.mozilla.org/en-US/docs/Web/CSS/aspect-ratio)
* [object-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit)
