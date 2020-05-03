---
title: "Cutter"
---

# Cutter

{{< featured type="Mixin" name="cutter" >}}
Cutter mixin helps you to **cut off** the corners of an element. Provides an easy to use one-line method to set the size of the cut, and the corners that you want to apply the effect.

{{< hint info >}}
The **first** value helps you select `top-left`, the **second** value `top-right`, the **third** value `bottom-right` and the **fourth** value `bottom-left` corners.
{{< /hint >}}

{{< /featured >}}

## Arguments

{{< arguments/table footnote="You can use `0` or `null` to skip styling the related corner.">}}
    {{< arguments/row name="--" type="number (with unit)" description="Accepts `one` or `four` values. The values must be separated by space. Use `null` value to **skip** corners of the box." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin and pass just `one` value to affect all the corners evenly.
{{< highlight scss >}}
.element{
    @include gls-cutter(30px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    clip-path: polygon(0 30px, 30px 0, calc(100% - 30px) 0, 100% 30px, 100% calc(100% - 30px), calc(100% - 30px) 100%, 30px 100%, 0 calc(100% - 30px));
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-color: #5bc0bb;
clip-path: polygon(0 30px, 30px 0, calc(100% - 30px) 0, 100% 30px, 100% calc(100% - 30px), calc(100% - 30px) 100%, 30px 100%, 0 calc(100% - 30px));
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Do as follow to target only the top corners.
{{< highlight scss >}}
.element{
    @include gls-cutter(30px 30px 0 0);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    clip-path: polygon(0 30px, 30px 0, calc(100% - 30px) 0, 100% 30px, 100% calc(100% - 0px), calc(100% - 0px) 100%, 0px 100%, 0 calc(100% - 0px));
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-color: #5bc0bb;
clip-path: polygon(0 30px, 30px 0, calc(100% - 30px) 0, 100% 30px, 100% calc(100% - 0px), calc(100% - 0px) 100%, 0px 100%, 0 calc(100% - 0px));
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use `null` to skip a corner as well! The following arrangement will target only the bottom corners.
{{< highlight scss >}}
.element{
    @include gls-cutter(null null 50px 50px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    clip-path: polygon(0 0px, 0px 0, calc(100% - 0px) 0, 100% 0px, 100% calc(100% - 50px), calc(100% - 50px) 100%, 50px 100%, 0 calc(100% - 50px));
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-color: #5bc0bb;
clip-path: polygon(0 0px, 0px 0, calc(100% - 0px) 0, 100% 0px, 100% calc(100% - 50px), calc(100% - 50px) 100%, 50px 100%, 0 calc(100% - 50px));
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try something really fancy!
{{< hint info >}}
For some reason, your design component might look different, but I'm sure you get the idea.
{{< /hint >}}
{{< highlight html >}}
<div class="element">
    <h2>It's a fancy looking title text!</h2>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
    height: 300px;
    display: flex;
    justify-content: center;
    background-color: #5bc0bb;
    @include gls-cutter(0 0 50% 50%);
    h2{
        color: white;
        font-size: 2.5em;
        text-align: center;
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    height: 200px;
    display: flex;
    justify-content: center;
    background-color: #5bc0bb;
    clip-path: polygon(0 0px, 0px 0, calc(100% - 0px) 0, 100% 0px, 100% calc(100% - 50%), calc(100% - 50%) 100%, 50% 100%, 0 calc(100% - 50%));
}
.element h2 {
    color: white;
    font-size: 2.5em;
    text-align: center;
}
{{< /highlight >}}
<div class="element">
    <h2>It's a fancy looking title text!</h2>
</div>
<style>
.element {
    height: 200px;
    display: flex;
    justify-content: center;
    background-color: #5bc0bb;
    clip-path: polygon(0 0px, 0px 0, calc(100% - 0px) 0, 100% 0px, 100% calc(100% - 50%), calc(100% - 50%) 100%, 50% 100%, 0 calc(100% - 50%));
}
.element h2 {
    color: white;
    font-size: 2.5em;
    text-align: center;
}
</style>
{{< /highlightwrap >}}
