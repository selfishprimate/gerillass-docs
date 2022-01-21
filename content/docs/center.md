---
title: "Center"
page_title: "Center Sass Mixin"
page_description: "Center Sass Mixin allows you to center selected elements both on the horizontal and vertical axes by using absolute positioning in CSS and Sass."
---

# Center

{{< mixin type="Mixin" name="center" >}}
**Center** Sass mixin allows you to center elements (**the elements that have `position` value either `absolute` or `fixed`**) on both the horizontal and vertical axes.
{{< hint info >}}
**Important:** You must declare either `position: absolute` or `position: fixed` style rule to the selected element to make this mixin work correctly. **The parent element's `position` value, which you'll be centering within must be other than `static`**.
{{< /hint >}}
{{< hint warning >}}
**Note that in mind** that because this mixin uses the CSS ‘**transform**’ property, this property will no longer be available for the selected element!
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Pass `both` value to center an element on both the horizontal and vertical axes, or do not pass at all.">}}
  {{< arguments/row name="$axis" type="string" description="Sets the axis of the alingment. Accepts `horizontal`, `vertical` and `both` values. The default value is set to `both`." >}}
{{< /arguments/table >}}


## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments **to center the selected element on both the horizontal and vertical axes**.
{{< highlight scss >}}
.parent-element {
  position: relative;
  .element{
    position: absolute;
    @include center;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
  position: relative;
}
.parent-element .element {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
}
{{< /highlight >}}
<style>
.parent-element.example01 .element {
  position: absolute;
  top: 50%;
  left: 50%;
  -webkit-transform: translateX(-50%) translateY(-50%);
  transform: translateX(-50%) translateY(-50%);
}
</style>
<div class="parent-element sandbox large example01">
  <h2 class="element">Gerillass</h2>
</div>
{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
Let's **center** the selected element on **horizontal axis only**.
{{< highlight scss >}}
.parent-element {
  position: relative;
  .element{
    position: absolute;
    @include center(horizontal);
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
  position: relative;
}
.parent-element .element {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}
{{< /highlight >}}
<style>
.parent-element.example02 .element {
  position: absolute;
  left: 50%;
  -webkit-transform: translateX(-50%);
  transform: translateX(-50%);
}
</style>
<div class="parent-element sandbox large example02">
  <h2 class="element">Gerillass</h2>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's **center** the selected element on **vertical axis only**.
{{< highlight scss >}}
.parent-element {
  position: relative;
  .element{
    position: absolute;
    @include center(vertical);
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
  position: relative;
}
.parent-element .element {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}
{{< /highlight >}}
<style>
.parent-element.example03 .element {
  position: absolute;
  top: 50%;
  -webkit-transform: translateY(-50%);
  transform: translateY(-50%);
}
</style>
<div class="parent-element sandbox large example03">
    <h2 class="element">Gerillass</h2>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's pass `both` value to **center** the selected element **on both the horizontal and vertical axes**.
{{< highlight scss >}}
.parent-element {
  position: relative;
  .element{
    position: absolute;
    @include center(both);
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
  position: relative;
}
.parent-element .element {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
}
{{< /highlight >}}
<style>
.parent-element.example04 .element {
  position: absolute;
  top: 50%;
  left: 50%;
  -webkit-transform: translateX(-50%) translateY(-50%);
  transform: translateX(-50%) translateY(-50%);
}
</style>
<div class="parent-element sandbox large example04">
  <h2 class="element">Gerillass</h2>
</div>
<style>
.parent-element{
  position: relative;
  background-color: rgba(255, 192, 203, 0.5);
  padding: 20px;
}
.parent-element .element{
  margin: 0;
  font-size: 3em;
}
</style>
{{< /highlightwrap >}}
