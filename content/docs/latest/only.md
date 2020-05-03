---
title: "Only"
---

# Only

{{< featured type="Mixin" name="only" >}}
This mixin helps you to filter elements that match based on their position among a group of siblings and apply your style rules to **only** those elements.
{{< hint info >}}
You can pass a **string** value to target elements by their `id`, `class` and `pseudo-class` selector. Or you can pass a **number** (or **multiple numbers** seperated by comma) to get the items based on their index position in the list.
{{< /hint >}}
{{< /featured >}}

## Arguments

{{< arguments/table footnote="**Important:** Passing multiple arguments is only for numeric values and the values must be comma-separated.">}}
    {{< arguments/row name="--" type="string" description="The pseudo-class, class or id selectors. Accepts `first`, `last`, `odd`, `even` and class or id selectors." >}}
    {{< arguments/row name="--" type="number" description="The index number of the element(s) in the list. It is also possible to make multiple selections." >}}
{{< /arguments/table >}}

## Examples

Suppose you have a group of items like in the example below and you want to make some style changes only for some of them.

{{< highlight html >}}
<div class="list-wrapper">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlight >}}

{{< highlightwrap class="example">}}
Let's start with the **first** one!
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-only(first) {
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:first-of-type {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example01 .list-item:first-of-type {
    background-color: #5bc0bb;
    color: white;
}
</style>
<div class="list-wrapper example01">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try to get the **last item** in the list.
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-only(last) {
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:last-of-type {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example02 .list-item:last-of-type {
    background-color: #5bc0bb;
    color: white;
}
</style>
<div class="list-wrapper example02">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
Now, let's target the **second** item in the list.
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-only(2) {
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:first-of-type {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example03 .list-item:nth-of-type(2) {
    background-color: #5bc0bb;
    color: white;
}
</style>
<div class="list-wrapper example03">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlightwrap >}}



{{< highlightwrap class="example">}}
Let’s get those elements whose numeric position is odd (e.g. 1, 3, 5, ...).
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-only(odd){
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:nth-of-type(odd) {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example04 .list-item:nth-of-type(odd) {
    background-color: #5bc0bb;
    color: white;
}
</style>
<div class="list-wrapper example04">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try something really fancy!
{{< hint info >}}
Remember that when you make a multiple selection the arguments you pass must be numbers and separated by comma.
{{</ hint >}}
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-only(4, 5, 6) {
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:nth-of-type(4), 
.list-wrapper .list-item:nth-of-type(5), 
.list-wrapper .list-item:nth-of-type(6) {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example05 .list-item:nth-of-type(4), 
.list-wrapper.example05 .list-item:nth-of-type(5), 
.list-wrapper.example05 .list-item:nth-of-type(6) {
    background-color: #5bc0bb;
    color: white;
}
</style>
<div class="list-wrapper example05">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlightwrap >}}

