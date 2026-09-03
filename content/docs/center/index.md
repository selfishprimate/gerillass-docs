---
title: "Center"
page_title: "Center Sass Mixin"
page_description: "The Center Sass mixin allows you to center selected elements on both the horizontal and vertical axes using absolute positioning in CSS and Sass."
---

# Center

{{< mixin type="Mixin" name="center" >}}
The **Center** Sass mixin allows you to center elements (**those with a `position` value of either `absolute` or `fixed`**) on both the horizontal and vertical axes.
{{< hint info >}}
**Important:** You must set either `position: absolute` or `position: fixed` on the selected element to make this mixin work correctly. **The parent element you are centering within must have a `position` value other than `static`.**
{{< /hint >}}
{{< hint warning >}}
**Keep in mind** that because this mixin uses the CSS **transform** property, that property will no longer be available for the selected element!
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Pass the `both` value to center an element on both the horizontal and vertical axes, or pass nothing at all.">}}
  {{< arguments/row name="$axis" type="string" description="Sets the axis of the alignment. Accepts the values `horizontal`, `vertical`, and `both`. The default value is `both`." >}}
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
Let's **center** the selected element on the **horizontal axis only**.
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
Now let's **center** the selected element on the **vertical axis only**.
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
Now let's pass the `both` value to **center** the selected element **on both the horizontal and vertical axes**.
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
