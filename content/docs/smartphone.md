---
title: "Smartphone"
site_title: "Smartphone Sass Mixin"
site_description: "There will be times when you need to style elements only for one particular smartphone model. Smartphone Sass mixin helps you to achieve that."
---

# Smartphone

{{< mixin type="Mixin" name="smartphone" >}}
There will be times when you need to style elements only for one particular smartphone model. **Smartphone** Sass mixin helps you to achieve that.
{{< hint info >}}
**Tip:** There are predefined values for commonly used smartphone models in the `_map-for-smartphones.scss` file. **You can add another model specifications here to expand the list if you like**.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="The string values can be pass with or without the quotation marks." >}}
  {{< arguments/row name="$device" type="string" description="Accepts the name of a smartphone model. Predefined values are `iPhone4`, `iPhone-SE`, `iPhone5-SE`, `iPhone6`, `iPhone6-Plus`, `iPhone7`, `iPhone7-Plus`, `iPhone8`, `iPhone8-Plus`, `iPhone11`, `iPhone11-Pro`, `iPhone11-Pro-Max`, `iPhoneX`, `Galaxy-S7`, `Galaxy-S8`, `Galaxy-S8-Plus`, `Galaxy-S10`." >}}
  {{< arguments/row name="$orientation" type="string" description="Accepts two values: `portrait` or `landscape`. The default value is set to `portrait`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
First, call the mixin and pass only one value for the `$device` model name. Unless you pass a value for `$orientation`, it will be `portrait`.
{{< highlight scss >}}
.element {
  @include smartphone(iPhone8) {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media only screen and (device-width: 375px) and (device-height: 667px) and (orientation: portrait) {
  .element {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try to pass two arguments: one for the name of the `$device` model, the other is for the `$orientation`.
{{< highlight scss >}}
.element{
  @include smartphone(iPhone8-Plus, landscape){
    background-color: teal;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media only screen and (device-width: 736px) and (device-height: 414px) and (orientation: landscape) {
  .element {
    background-color: teal;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}


