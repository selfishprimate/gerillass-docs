---
title: "Fluid"
page_title: "Fluid Sass Function"
page_description: "The fluid Sass function returns a clamp() value that grows with the viewport between two widths, then stops. It keeps a rem term so the value still responds to browser text zoom."
page_keywords: "Fluid Typography Sass, CSS clamp Function, Fluid Type Scale, Sass clamp, Responsive Font Size, WCAG 1.4.4 Resize Text, vw Font Size Accessibility, Fluid Spacing CSS"
---

# Fluid

{{< function type="Function" name="fluid" file="fluid" >}}
A value that grows with the viewport between two widths and then stops. `fluid(24px, 48px)` is `24px` on a small screen, `48px` on a large one, and a straight line between the two.

{{< hint danger >}}
**This is why the function exists.** Written by hand, a fluid value usually comes out as pure `vw`, and a `vw`-only value ignores browser text zoom. Measured: raising the root font size, which is exactly what text zoom does, moved the value this function returns from **20.83px to 34.17px**, while an equivalent `vw`-only value stayed at **19.74px** and did not respond at all. A `vw`-only value fails [WCAG 1.4.4](https://www.w3.org/WAI/WCAG21/Understanding/resize-text.html). The preferred value here keeps a `rem` term so it does not.
{{< /hint >}}

{{< hint info >}}
**It is a function, not a mixin, so there is no `@include`.** The hard part is the value, and a value belongs to any property. `font-size` is the obvious one, but `padding`, `gap` and `margin` take it just as well.
{{< /hint >}}
{{< /function >}}

## How the value is built

The preferred value is the line through `(min-viewport, min)` and `(max-viewport, max)`.

{{< highlightwrap class="terminal">}}
{{< highlight nix >}}
slope     = (max - min) / (max-viewport - min-viewport)
intercept = min - slope * min-viewport
preferred = intercept + slope * 100vw
{{< /highlight >}}
{{< /highlightwrap >}}

Checked against hand arithmetic at a real 900px viewport: the floor came out at 16.00px against 16.00 expected, the ceiling at 24.00 against 24.00, and an interpolated value at 19.52 against 19.52.

## Arguments

{{< arguments/table footnote="Lengths must be px or rem. Other units are refused, because the function has to convert between them to build the line.">}}
  {{< arguments/row name="$min" type="number (with unit)" description="Accepts a length in px or rem, the value at `$min-viewport`." >}}
  {{< arguments/row name="$max" type="number (with unit)" description="Accepts a length in px or rem, the value at `$max-viewport`, no smaller than `$min`." >}}
  {{< arguments/row name="$min-viewport (320px)" type="number (with unit)" description="Accepts a length in px or rem, the width below which the value stops shrinking." >}}
  {{< arguments/row name="$max-viewport (1280px)" type="number (with unit)" description="Accepts a length in px or rem, larger than `$min-viewport`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
A heading that scales between the two default viewport widths.
{{< highlight scss >}}
.title {
  font-size: fluid(24px, 48px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.title {
  font-size: clamp(1.5rem, 1rem + 2.5vw, 3rem);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Your own viewport range, and values given in `rem`.
{{< highlight scss >}}
.title {
  font-size: fluid(1rem, 3rem, 320px, 1200px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.title {
  font-size: clamp(1rem, 0.2727rem + 3.6364vw, 3rem);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Not only for type. Two calls in one shorthand give a padding that scales on both axes.
{{< highlight scss >}}
.section {
  padding: fluid(16px, 64px) fluid(8px, 40px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.section {
  padding: clamp(1rem, 0rem + 5vw, 4rem) clamp(0.5rem, -0.1667rem + 3.3333vw, 2.5rem);
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
A grid gap that opens up on wider screens.
{{< highlight scss >}}
.stack {
  gap: fluid(0.5rem, 2rem);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.stack {
  gap: clamp(0.5rem, 0rem + 2.5vw, 2rem);
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing a value that never changes.

{{< highlightwrap >}}
The viewport range the wrong way round.
{{< highlight scss >}}
.title {
  font-size: fluid(16px, 24px, 1280px, 320px);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `fluid` needs $min-viewport to be smaller than $max-viewport, and was given 1280px and 320px.
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
A maximum smaller than the minimum, which `clamp()` would silently flatten.
{{< highlight scss >}}
.title {
  font-size: fluid(40px, 20px);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `fluid` needs $min to be no larger than $max, and was given 40px and 20px. clamp() would return the floor at every width, so the value would never grow.
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
Unitless numbers.
{{< highlight scss >}}
.title {
  font-size: fluid(16, 24);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `16` is not a valid $min for `fluid`. Pass a length in px or rem.
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
`em`, which is relative to the element's own font size and so cannot be resolved into the line.
{{< highlight scss >}}
.title {
  font-size: fluid(1em, 2em);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `1em` is not a valid $min for `fluid`. Pass a length in px or rem, not em.
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Links
* [clamp()](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp)
* [WCAG 1.4.4 Resize Text](https://www.w3.org/WAI/WCAG21/Understanding/resize-text.html)
