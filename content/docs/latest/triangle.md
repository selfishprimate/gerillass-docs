---
title: "Triangle"
---

# Triangle

{{< mixin type="Mixin" name="triangle" >}}
**Triangle** Sass mixin helps you to generate triangles.
{{< hint info >}}
**Tip:** Works best with the text based elements to point a direction to make user take action (e.g. dropdown menu labels). Especially very useful when you apply it to the selected element's `::before` or `::after` pseudo-elements.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="When you pass `top`, `right`, `bottom`, `left` values for **`$direction`** argument you can pass two values to resize the triangle. **The first value controls the width of the triangle while the second controls the height**. ">}}
    {{< arguments/row name="$direction" type="string" description="Sets the direction of the triangle. Accepts `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left` values." >}}
    {{< arguments/row name="$color" type="color" description="The color of the triangle." >}}
    {{< arguments/row name="$size" type="number (with unit)" description="The size of the triangle. Multiple values must be seperated by space." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Suppose you have an expandable box and you want users to click a label to expand it! **Let's apply the mixin to the `::after` pseudo-element of the selected element**.

{{< highlight html >}}
<div class="element">Click here to expand it!</div>
{{< /highlight >}}

{{< highlight scss >}}
.element {
    &::after {
        @include gls-triangle;
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
    content: "";
    height: 0;
    width: 0;
    display: inline-block;
    border-style: solid;
    border-color: black transparent transparent;
    border-width: 8px 5px 0;
}
{{< /highlight >}}
<style>
.element.example01::after {
    content: "";
    height: 0;
    width: 0;
    display: inline-block;
    border-style: solid;
    border-color: black transparent transparent;
    border-width: 8px 5px 0;
}
</style>
<div class="element example01">Click here to expand it!</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's **change the `$color` and the `$size`** of the triangle, and seperate it from the text by **passing a decleration block into the mixin**.

{{< highlight scss >}}
.element {
    &::after {
        @include gls-triangle(
            $color: crimson,
            $size: 6px
        ) {
            margin-left: 6px;
        };
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
    content: "";
    height: 0;
    width: 0;
    display: inline-block;
    border-style: solid;
    border-color: crimson transparent transparent;
    border-width: 6px 3px 0;
    margin-left: 6px;
}
{{< /highlight >}}
<style>
.element.example02::after {
    content: "";
    height: 0;
    width: 0;
    display: inline-block;
    border-style: solid;
    border-color: crimson transparent transparent;
    border-width: 6px 3px 0;
    margin-left: 6px;
}
</style>
<div class="element example02">Click here to expand it!</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
When you pass one of the `top`, `right`, `bottom` or `left` values for `$direction` argument, you can pass secondary value to resize the triangle. First value controls the width of the triangle and the second is for height.
{{< highlight scss >}}
.element{
    &::after {
        @include gls-triangle(
            $direction: "bottom",
            $color: crimson,
            $size: 10px 6px
        ) {
            position: relative;
            margin-left: 6px;
            top: -2px;
        };
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
    content: "";
    height: 0;
    width: 0;
    display: inline-block;
    border-style: solid;
    border-color: crimson transparent transparent;
    border-width: 6px 5px 0;
    position: relative;
    margin-left: 6px;
    top: -2px;
}
{{< /highlight >}}
<style>
.element.example03::after {
    content: "";
    height: 0;
    width: 0;
    display: inline-block;
    border-style: solid;
    border-color: crimson transparent transparent;
    border-width: 6px 5px 0;
    position: relative;
    margin-left: 6px;
    top: -2px;
}
</style>
<div class="element example03">Click here to expand it!</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can apply the mixin not only to the pseudo-elements but to the selected element's itself.
{{< highlight scss >}}
.element{
    @include gls-triangle(
        $direction: "top",
        $color: crimson,
        $size: 100px 50px
    )
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    content: "";
    height: 0;
    width: 0;
    display: inline-block;
    border-style: solid;
    border-color: transparent transparent crimson;
    border-width: 0 50px 50px;
}
{{< /highlight >}}
<style>
.element.example04 {
  content: "";
  height: 0;
  width: 0;
  display: inline-block;
  border-style: solid;
  border-color: transparent transparent crimson;
  border-width: 0 50px 50px;
}
</style>
<div class="element example04"></div>
{{< /highlightwrap >}}
