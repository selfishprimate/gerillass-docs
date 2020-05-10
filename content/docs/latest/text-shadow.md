---
title: "Text Shadow"
---

# Text Shadow

{{< featured type="Mixin" name="text-shadow" >}}
**Text Shadow** Sass mixin helps you to add shadow to texts. Accepts comma-seperated list of shadow or a single shadow value that can be multiplied optionally. **Provides an easy to use one-line method**.
{{< hint info >}}
The first three (`$direction`, `$color`, `$size`) are the required arguments and they must be ordered as follow: @include gls-text-shadow(**bottom red 20px**). You can't use these three interchangeably.
{{< /hint >}}
{{< /featured >}}

## Arguments

{{< arguments/table footnote="**Design Tip:** You can add multi layered shadows to create more fancy stuff. Just seperate each shadow layer by comma. For more see the [examples](#examples).">}}
    {{< arguments/row name="$direction" type="string" description="Sets the direction of the shadow. Accepts `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left`." >}}
    {{< arguments/row name="$color" type="color value" description="Sets the color of the shadow." >}}
    {{< arguments/row name="$size" type="number (with unit)" description="Sets how far the shadow will be from the text. When used with `$fill`, it also determines how many times the shadow will be multiplied." >}}
    {{< arguments/row name="$blur" type="number (with unit)" description="The `$blur` argument is optional. Sets the blur value of the shadow. Default value is set to `null`." >}}
    {{< arguments/row name="$fill" type="boolean" description="This makes shadow fill the gap between the text and the shadow. It is optional and **should always be at the end** The default value is set to `false`." >}}
{{< /arguments/table >}}

{{< hint danger >}}
**Important:** If used, the `$fill` argument should always be at the end.
{{< /hint >}}

## Examples

{{< highlightwrap class="example">}}
Let's start with some basic shadow arrangements.
{{< highlight scss >}}
.element{
    @include gls-text-shadow(bottom rgba(black, 0.3) 6px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    text-shadow: 0 6px rgba(0, 0, 0, 0.3);
}
{{< /highlight >}}
<div class="text-shadow-container">
    <h1 style="text-shadow: 0 6px rgba(0, 0, 0, 0.3);">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's **add some $blur** to the shadow.
{{< highlight scss >}}
.element{
    @include gls-text-shadow(bottom rgba(black, 0.3) 6px 4px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    text-shadow: 0 6px 4px rgba(0, 0, 0, 0.3);
}
{{< /highlight >}}
<div class="text-shadow-container">
    <h1 style="text-shadow: 0 6px 4px rgba(0, 0, 0, 0.3);">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, to understand what `$fill` is for, let's try one more time without the `$fill` argument and examine the CSS output. 
{{< highlight scss >}}
.element{
    @include gls-text-shadow(bottom #5bc0bb 30px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    text-shadow: 0 20px #5bc0bb;
}
{{< /highlight >}}
<div class="text-shadow-container">
    <h1 style="text-shadow: 0 20px #5bc0bb;">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's pass the `true` value at the end of the argument list and watch the CSS output carefully. Because here's where the magic starts.
{{< hint info >}}
It takes the shadow and increments it as much as the amount of the `$size` value to **fill the gap between the actual text and the shadow's end-point**.
{{< /hint >}}
{{< highlight scss >}}
.element{
    @include gls-text-shadow(bottom #5bc0bb 30px true);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    text-shadow: 0 1px #5bc0bb, 0 2px #5bc0bb, 0 3px #5bc0bb, 0 4px #5bc0bb, 0 5px #5bc0bb, 0 6px #5bc0bb, 0 7px #5bc0bb, 0 8px #5bc0bb, 0 9px #5bc0bb, 0 10px #5bc0bb, 0 11px #5bc0bb, 0 12px #5bc0bb, 0 13px #5bc0bb, 0 14px #5bc0bb, 0 15px #5bc0bb, 0 16px #5bc0bb, 0 17px #5bc0bb, 0 18px #5bc0bb, 0 19px #5bc0bb, 0 20px #5bc0bb, 0 21px #5bc0bb, 0 22px #5bc0bb, 0 23px #5bc0bb, 0 24px #5bc0bb, 0 25px #5bc0bb, 0 26px #5bc0bb, 0 27px #5bc0bb, 0 28px #5bc0bb, 0 29px #5bc0bb, 0 30px #5bc0bb;
}
{{< /highlight >}}
<div class="text-shadow-container">
    <h1 style="text-shadow: 0 1px #5bc0bb, 0 2px #5bc0bb, 0 3px #5bc0bb, 0 4px #5bc0bb, 0 5px #5bc0bb, 0 6px #5bc0bb, 0 7px #5bc0bb, 0 8px #5bc0bb, 0 9px #5bc0bb, 0 10px #5bc0bb, 0 11px #5bc0bb, 0 12px #5bc0bb, 0 13px #5bc0bb, 0 14px #5bc0bb, 0 15px #5bc0bb, 0 16px #5bc0bb, 0 17px #5bc0bb, 0 18px #5bc0bb, 0 19px #5bc0bb, 0 20px #5bc0bb, 0 21px #5bc0bb, 0 22px #5bc0bb, 0 23px #5bc0bb, 0 24px #5bc0bb, 0 25px #5bc0bb, 0 26px #5bc0bb, 0 27px #5bc0bb, 0 28px #5bc0bb, 0 29px #5bc0bb, 0 30px #5bc0bb;">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can **add alpha value to the colors** to soften the shadow.
{{< highlight scss >}}
.element{
    @include gls-text-shadow(bottom rgba(#5bc0bb, 0.04) 30px true);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    text-shadow: 0 1px rgba(91, 192, 187, 0.04), 0 2px rgba(91, 192, 187, 0.04), 0 3px rgba(91, 192, 187, 0.04), 0 4px rgba(91, 192, 187, 0.04), 0 5px rgba(91, 192, 187, 0.04), 0 6px rgba(91, 192, 187, 0.04), 0 7px rgba(91, 192, 187, 0.04), 0 8px rgba(91, 192, 187, 0.04), 0 9px rgba(91, 192, 187, 0.04), 0 10px rgba(91, 192, 187, 0.04), 0 11px rgba(91, 192, 187, 0.04), 0 12px rgba(91, 192, 187, 0.04), 0 13px rgba(91, 192, 187, 0.04), 0 14px rgba(91, 192, 187, 0.04), 0 15px rgba(91, 192, 187, 0.04), 0 16px rgba(91, 192, 187, 0.04), 0 17px rgba(91, 192, 187, 0.04), 0 18px rgba(91, 192, 187, 0.04), 0 19px rgba(91, 192, 187, 0.04), 0 20px rgba(91, 192, 187, 0.04), 0 21px rgba(91, 192, 187, 0.04), 0 22px rgba(91, 192, 187, 0.04), 0 23px rgba(91, 192, 187, 0.04), 0 24px rgba(91, 192, 187, 0.04), 0 25px rgba(91, 192, 187, 0.04), 0 26px rgba(91, 192, 187, 0.04), 0 27px rgba(91, 192, 187, 0.04), 0 28px rgba(91, 192, 187, 0.04), 0 29px rgba(91, 192, 187, 0.04), 0 30px rgba(91, 192, 187, 0.04);
}
{{< /highlight >}}
<div class="text-shadow-container">
    <h1 style="text-shadow: 0 1px rgba(91, 192, 187, 0.04), 0 2px rgba(91, 192, 187, 0.04), 0 3px rgba(91, 192, 187, 0.04), 0 4px rgba(91, 192, 187, 0.04), 0 5px rgba(91, 192, 187, 0.04), 0 6px rgba(91, 192, 187, 0.04), 0 7px rgba(91, 192, 187, 0.04), 0 8px rgba(91, 192, 187, 0.04), 0 9px rgba(91, 192, 187, 0.04), 0 10px rgba(91, 192, 187, 0.04), 0 11px rgba(91, 192, 187, 0.04), 0 12px rgba(91, 192, 187, 0.04), 0 13px rgba(91, 192, 187, 0.04), 0 14px rgba(91, 192, 187, 0.04), 0 15px rgba(91, 192, 187, 0.04), 0 16px rgba(91, 192, 187, 0.04), 0 17px rgba(91, 192, 187, 0.04), 0 18px rgba(91, 192, 187, 0.04), 0 19px rgba(91, 192, 187, 0.04), 0 20px rgba(91, 192, 187, 0.04), 0 21px rgba(91, 192, 187, 0.04), 0 22px rgba(91, 192, 187, 0.04), 0 23px rgba(91, 192, 187, 0.04), 0 24px rgba(91, 192, 187, 0.04), 0 25px rgba(91, 192, 187, 0.04), 0 26px rgba(91, 192, 187, 0.04), 0 27px rgba(91, 192, 187, 0.04), 0 28px rgba(91, 192, 187, 0.04), 0 29px rgba(91, 192, 187, 0.04), 0 30px rgba(91, 192, 187, 0.04);">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's **add multiple shadow values** with different `$direction`, `$color`, `$size` values.
{{< highlight scss >}}
.element{
    @include gls-text-shadow(
        top yellow 5px, 
        right lightseagreen 15px,
        bottom orange 5px, 
        left pink 15px,
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    text-shadow: 0 -5px yellow, 15px 0 lightseagreen, 0 5px orange, -15px 0 pink;
}
{{< /highlight >}}
<div class="text-shadow-container">
    <h1 style="text-shadow: 0 -5px yellow, 15px 0 lightseagreen, 0 5px orange, -15px 0 pink;">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's **add alpha value the colors** and set `$fill` option to `true` to make it look more sexy!
{{< highlight scss >}}
.element{
    @include gls-text-shadow(
        top rgba(yellow, 0.1) 10px true, 
        bottom rgba(orange, 0.1) 10px true, 
        left rgba(pink, 0.1) 10px true,
        right rgba(lightseagreen, 0.1) 10px true
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    text-shadow: 0 -1px rgba(255, 255, 0, 0.1), 0 -2px rgba(255, 255, 0, 0.1), 0 -3px rgba(255, 255, 0, 0.1), 0 -4px rgba(255, 255, 0, 0.1), 0 -5px rgba(255, 255, 0, 0.1), 0 -6px rgba(255, 255, 0, 0.1), 0 -7px rgba(255, 255, 0, 0.1), 0 -8px rgba(255, 255, 0, 0.1), 0 -9px rgba(255, 255, 0, 0.1), 0 -10px rgba(255, 255, 0, 0.1), 0 1px rgba(255, 165, 0, 0.1), 0 2px rgba(255, 165, 0, 0.1), 0 3px rgba(255, 165, 0, 0.1), 0 4px rgba(255, 165, 0, 0.1), 0 5px rgba(255, 165, 0, 0.1), 0 6px rgba(255, 165, 0, 0.1), 0 7px rgba(255, 165, 0, 0.1), 0 8px rgba(255, 165, 0, 0.1), 0 9px rgba(255, 165, 0, 0.1), 0 10px rgba(255, 165, 0, 0.1), -1px 0 rgba(255, 192, 203, 0.1), -2px 0 rgba(255, 192, 203, 0.1), -3px 0 rgba(255, 192, 203, 0.1), -4px 0 rgba(255, 192, 203, 0.1), -5px 0 rgba(255, 192, 203, 0.1), -6px 0 rgba(255, 192, 203, 0.1), -7px 0 rgba(255, 192, 203, 0.1), -8px 0 rgba(255, 192, 203, 0.1), -9px 0 rgba(255, 192, 203, 0.1), -10px 0 rgba(255, 192, 203, 0.1), 1px 0 rgba(32, 178, 170, 0.1), 2px 0 rgba(32, 178, 170, 0.1), 3px 0 rgba(32, 178, 170, 0.1), 4px 0 rgba(32, 178, 170, 0.1), 5px 0 rgba(32, 178, 170, 0.1), 6px 0 rgba(32, 178, 170, 0.1), 7px 0 rgba(32, 178, 170, 0.1), 8px 0 rgba(32, 178, 170, 0.1), 9px 0 rgba(32, 178, 170, 0.1), 10px 0 rgba(32, 178, 170, 0.1);
}
{{< /highlight >}}
<div class="text-shadow-container">
    <h1 style="text-shadow: 0 -1px rgba(255, 255, 0, 0.1), 0 -2px rgba(255, 255, 0, 0.1), 0 -3px rgba(255, 255, 0, 0.1), 0 -4px rgba(255, 255, 0, 0.1), 0 -5px rgba(255, 255, 0, 0.1), 0 -6px rgba(255, 255, 0, 0.1), 0 -7px rgba(255, 255, 0, 0.1), 0 -8px rgba(255, 255, 0, 0.1), 0 -9px rgba(255, 255, 0, 0.1), 0 -10px rgba(255, 255, 0, 0.1), 0 1px rgba(255, 165, 0, 0.1), 0 2px rgba(255, 165, 0, 0.1), 0 3px rgba(255, 165, 0, 0.1), 0 4px rgba(255, 165, 0, 0.1), 0 5px rgba(255, 165, 0, 0.1), 0 6px rgba(255, 165, 0, 0.1), 0 7px rgba(255, 165, 0, 0.1), 0 8px rgba(255, 165, 0, 0.1), 0 9px rgba(255, 165, 0, 0.1), 0 10px rgba(255, 165, 0, 0.1), -1px 0 rgba(255, 192, 203, 0.1), -2px 0 rgba(255, 192, 203, 0.1), -3px 0 rgba(255, 192, 203, 0.1), -4px 0 rgba(255, 192, 203, 0.1), -5px 0 rgba(255, 192, 203, 0.1), -6px 0 rgba(255, 192, 203, 0.1), -7px 0 rgba(255, 192, 203, 0.1), -8px 0 rgba(255, 192, 203, 0.1), -9px 0 rgba(255, 192, 203, 0.1), -10px 0 rgba(255, 192, 203, 0.1), 1px 0 rgba(32, 178, 170, 0.1), 2px 0 rgba(32, 178, 170, 0.1), 3px 0 rgba(32, 178, 170, 0.1), 4px 0 rgba(32, 178, 170, 0.1), 5px 0 rgba(32, 178, 170, 0.1), 6px 0 rgba(32, 178, 170, 0.1), 7px 0 rgba(32, 178, 170, 0.1), 8px 0 rgba(32, 178, 170, 0.1), 9px 0 rgba(32, 178, 170, 0.1), 10px 0 rgba(32, 178, 170, 0.1);">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can **use corners** as well.
{{< highlight scss >}}
.element{
    color: pink;
    @include gls-text-shadow(top-left crimson 15px true);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    color: pink;
    text-shadow: -1px -1px crimson, -2px -2px crimson, -3px -3px crimson, -4px -4px crimson, -5px -5px crimson, -6px -6px crimson, -7px -7px crimson, -8px -8px crimson, -9px -9px crimson, -10px -10px crimson, -11px -11px crimson, -12px -12px crimson, -13px -13px crimson, -14px -14px crimson, -15px -15px crimson;
}
{{< /highlight >}}
<div class="text-shadow-container">
    <h1 style="color: pink;text-shadow: -1px -1px crimson, -2px -2px crimson, -3px -3px crimson, -4px -4px crimson, -5px -5px crimson, -6px -6px crimson, -7px -7px crimson, -8px -8px crimson, -9px -9px crimson, -10px -10px crimson, -11px -11px crimson, -12px -12px crimson, -13px -13px crimson, -14px -14px crimson, -15px -15px crimson;">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Here's a good example about how very easily you can create artistic effects by using **Gerillass**. Just hover over the text below and click on it to see the effect!
{{< hint info >}}
Unless you overdo **Text Shadow** mixin, you can create marvelous effects.
{{< /hint >}}
{{< highlight scss >}}
.element{
    transition: .3s;
    @include gls-text-shadow(left gold 3px true);
    &:hover{
        @include gls-text-shadow(right gold 8px true);
    }
    &:active{
        @include gls-text-shadow(right deepskyblue 8px true);
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    transition: .3s;
    text-shadow: -1px 0 gold, -2px 0 gold, -3px 0 gold;
}
.element:hover {
    text-shadow: 1px 0 gold, 2px 0 gold, 3px 0 gold, 4px 0 gold, 5px 0 gold, 6px 0 gold, 7px 0 gold, 8px 0 gold;
}
.element:active {
    text-shadow: 1px 0 deepskyblue, 2px 0 deepskyblue, 3px 0 deepskyblue, 4px 0 deepskyblue, 5px 0 deepskyblue, 6px 0 deepskyblue, 7px 0 deepskyblue, 8px 0 deepskyblue;
}
{{< /highlight >}}
<style>
.example09 {
    transition: .3s;
    text-shadow: -1px 0 gold, -2px 0 gold, -3px 0 gold;
}
.example09:hover {
    text-shadow: 1px 0 gold, 2px 0 gold, 3px 0 gold, 4px 0 gold, 5px 0 gold, 6px 0 gold, 7px 0 gold, 8px 0 gold;
}
.example09:active {
    text-shadow: 1px 0 deepskyblue, 2px 0 deepskyblue, 3px 0 deepskyblue, 4px 0 deepskyblue, 5px 0 deepskyblue, 6px 0 deepskyblue, 7px 0 deepskyblue, 8px 0 deepskyblue;
}
</style>
<div class="text-shadow-container">
    <h1 class="example09">Text Shadow is Awesome!</h1>
</div>
{{< /highlightwrap >}}

Examples are endless. **Just use your imagination.**












