---
title: "Position"
site_title: "Position Sass Mixin"
site_description: "Position Sass mixin provides a one-line method to rapidly set both the position and the offset properties of a selected element."
---

# Position

{{< mixin type="Mixin" name="position" >}}
**Position Sass mixin** provides a one-line method to rapidly set both the position and the offset properties of a selected element.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="To learn more about the CSS Shorthand Properties check out the links at the end of this page.">}}
  {{< arguments/row name="$position" type="string" description="This option sets the `position` property of a selected element(s). Accepts `static`, `relative`, `fixed`, `absolute`, `sticky` CSS values. The default value is set to `absolute`." >}}
  {{< arguments/row name="$offsets" type="list" description="Accepts a list of values to set the offset of the edges of the box. Uses CSS shorthand method. The default value is set to `0`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Call the mixin without passing any arguments to see the default values that it generates.
{{< highlight scss >}}
.element{
  @include position;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's set the position value to `fixed` and leave the offset values as they are.
{{< highlight scss >}}
.element{
  @include position(fixed);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Changin the offset values is easy. Note that the multiple offset values that you pass must be seperated by space.
{{< highlight scss >}}
.element{
  @include position(fixed, 10px 10px 10px 50px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: fixed;
  top: 10px;
  right: 10px;
  bottom: 10px;
  left: 50px;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use the `null` value to skip positioning some particular edges of an element.
{{< highlight scss >}}
.element{
  @include position(absolute, null 16px 16px 16px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  position: absolute;
  right: 16px;
  bottom: 16px;
  left: 16px;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Articles
* [CSS Shorthand Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties)
* [Introduction to CSS Shorthand](https://www.sitepoint.com/introduction-css-shorthand/)
