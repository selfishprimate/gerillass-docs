---
title: "Tablet"
---

# Tablet

{{< mixin type="Mixin" name="tablet" >}}
There will be times when you need to style elements only for one particular tablet model. **Tablet** Sass mixin helps you to achieve that.
{{< hint info >}}
**Tip:** There are predefined values for commonly used tablet models in the `_map-for-tablets.scss` file. **You can add another model specifications here to expand the list if you like**.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="The string values can be pass with or without the quotation marks." >}}
  {{< arguments/row name="$device" type="string" description="Accepts the name of a tablet model. Predefined values are `iPadMini`, `iPad`, `iPadAir`, `iPadPro`, `Nexus7`, `Nexus9`, `Nexus10`." >}}
  {{< arguments/row name="$orientation" type="string" description="Accepts two values: `portrait` or `landscape`. The default value is set to `portrait`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
First, call the mixin and pass only one value for the `$device` model name. Unless you pass a value for `$orientation`, it will be `portrait`.
{{< highlight scss >}}
.element {
  @include tablet(iPad) {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media only screen and (device-width: 810px) and (device-height: 1080px) and (orientation: portrait) {
  .element {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try to pass two arguments: one for the name of the `$device` model, the other is for the `$orientation`.
{{< highlight scss >}}
.element {
  @include tablet(Nexus10, landscape) {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media only screen and (device-width: 1280px) and (device-height: 800px) and (orientation: landscape) {
  .element {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}


