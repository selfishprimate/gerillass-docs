---
title: "isGutter"
page_title: "isGutter Sass Function"
page_description: "True for anything that can sit where a CSS length is expected: a number, a calculation, or a CSS function such as var()."
page_keywords: "Gerillass isGutter, Sass isGutter, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# isGutter

{{< function type="Function" name="isGutter" file="is-gutter" >}}
True for anything that can sit where a CSS length is expected: a number, a calculation, or a CSS function such as var().
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$value" type="value" description="Accepts any value." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Accepting var() and calc() where a length is expected.
{{< highlight scss >}}
@mixin stack($gap) {
  @if not isGutter($gap) {
    @error "`#{$gap}` cannot be used as a gap.";
  }
  display: grid;
  gap: $gap;
}
.stack {
  @include stack(var(--gap));
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.stack {
  display: grid;
  gap: var(--gap);
}
{{< /highlight >}}
{{< /highlightwrap >}}
