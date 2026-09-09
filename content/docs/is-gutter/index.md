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
{{< highlight scss >}}
.element {
  --x: #{isGutter(20px)};
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  --x: true;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
{{< highlight scss >}}
.element {
  --x: #{isGutter(var(--gap))};
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  --x: true;
}
{{< /highlight >}}
{{< /highlightwrap >}}
