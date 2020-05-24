---
title: "Border Radius"
---

# Border Radius

{{< mixin type="Mixin" name="border-radius" >}}
**Border Radius** Sass mixin helps you to rounds the corner(s) of an element. You can pass one value (with unit) to style all the corners equally or you can use CSS shorthand property to style each corner differently. For more see [the examples.](#examples)
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
    {{< arguments/row name="$corner" type="string" description="It allows you to choose the corners of an element that you want to apply style rules. Accepts the following values: `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left`, `cross-left`, `cross-right`, `all`." >}}
    {{< arguments/row name="$value" type="number (with unit)" description="Size of the border radius that will be applied." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply pass a value to target all the corners of an element and style them equally.
{{< highlight scss >}}
.element{
    @include gls-border-radius(20px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    border-radius: 20px;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-color: #5bc0bb;border-radius: 20px;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's pass two values: first one is `top` to target only top corners of a selected element and second one is `40px` for the size of the radius. 
{{< highlight scss >}}
.element{
    @include gls-border-radius(top, 40px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    border-top-left-radius: 40px;
    border-top-right-radius: 40px;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-color:#5bc0bb;border-top-left-radius: 40px;border-top-right-radius: 40px;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try to target right corners.
{{< hint info >}}
Just to remind you once more these are the predefined values to target the corners: `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left`, `left`, `top-left`, `cross-left`, `cross-right`, `all`.
{{< /hint >}}
{{< highlight scss >}}
.element{
    @include gls-border-radius(right, 40px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    border-top-right-radius: 40px;
    border-bottom-right-radius: 40px;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-color:#5bc0bb;border-top-right-radius: 40px;border-bottom-right-radius: 40px;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try the `cross-left` or `cross-right` values ​​so that you can target the corners diagonally.
{{< highlight scss >}}
.element{
    @include gls-border-radius(cross-left, 40px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    border-top-left-radius: 40px;
    border-bottom-right-radius: 40px;
}
{{< /highlight >}}
{{< sandbox class="medium" >}}
background-color:#5bc0bb;border-top-left-radius: 40px;border-bottom-right-radius: 40px;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use the CSS shorthand method to pass different radius size values for different corners.
{{< highlight scss >}}
.element{
    @include gls-border-radius(25px 50px 100px 150px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    border-radius: 25px 50px 100px 150px;
}
{{< /highlight >}}
{{< sandbox class="large" >}}
background-color:#5bc0bb;border-radius: 25px 50px 100px 150px;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's **pass four values** again but this time we're going to **seperate them by comma** to try something different.
{{< highlight scss >}}
.element{
    @include gls-border-radius(25px, 50px, 100px, 150px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    border-top-left-radius: 25px;
    border-top-right-radius: 50px;
    border-bottom-right-radius: 100px;
    border-bottom-left-radius: 150px;
}
{{< /highlight >}}
{{< sandbox class="large" >}}
background-color:#5bc0bb;border-top-left-radius: 25px;border-top-right-radius: 50px;border-bottom-right-radius: 100px;border-bottom-left-radius: 150px;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
For each argument you can pass a second argument next to it to bend the curve.
{{< highlight scss >}}
.element{
    @include gls-border-radius(100px 40px, 50px 20%, 100px 30%, 150px 2rem);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    border-top-left-radius: 100px 40px;
    border-top-right-radius: 50px 20%;
    border-bottom-right-radius: 100px 30%;
    border-bottom-left-radius: 150px 2rem;
}
{{< /highlight >}}
{{< sandbox class="large" >}}
background-color:#5bc0bb;border-top-left-radius: 100px 40px;border-top-right-radius: 50px 20%;border-bottom-right-radius: 100px 30%;border-bottom-left-radius: 150px 2rem;
{{< /sandbox >}}
{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
Use `null` to skip a corner!
{{< highlight scss >}}
.element{
    @include gls-border-radius(null, null, 100px 30%, 150px 2rem);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    border-bottom-right-radius: 100px 30%;
    border-bottom-left-radius: 150px 2rem;
}
{{< /highlight >}}
{{< sandbox class="large" >}}
background-color:#5bc0bb;border-bottom-right-radius: 100px 30%;border-bottom-left-radius: 150px 2rem;
{{< /sandbox >}}
{{< /highlightwrap >}}



