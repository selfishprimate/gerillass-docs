---
title: "Except"
---

# Except

{{< mixin type="Mixin" name="except" >}}
**Except** Sass mixin helps you to target elements that you do not want to apply style changes to that you want for other elements in the list.
{{< hint info >}}
You can pass a **string** value to target elements by their `id`, `class` and `pseudo-class` selector. Or you can pass a **number** (or **multiple numbers** seperated by comma) to get the items based on their index position in the list.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="**Important:** Passing multiple arguments is only for numeric values and the values must be comma-separated.">}}
    {{< arguments/row name="--" type="string" description="The pseudo-class, class or id selectors. Accepts `first`, `last`, `odd`, `even` and class or id selectors." >}}
    {{< arguments/row name="--" type="number" description="The index number of the element(s) in the list. It is also possible to make multiple selections." >}}
{{< /arguments/table >}}

## Examples

Let's say you have a list of items wrapped by a container. Just like the example below. Now, you want to apply some style changes to all of them, however, **except** for one or more ...

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
Let's exclude the **first** one!
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-except(first){
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(:first-of-type) {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example01 .list-item:not(:first-of-type) {
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
Now, let's try to exclude the **last item** in the list.
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-except(last){
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(:last-of-type) {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example02 .list-item:not(:last-of-type) {
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
Now, let's exclude the **third** item in the list.
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-except(3){
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(:nth-of-type(3)) {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example03 .list-item:not(:nth-of-type(3)) {
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
Let’s exclude those elements whose numeric position is even (e.g. 2, 4, 6, ...).
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-except(even){
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(:nth-of-type(even)) {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example04 .list-item:not(:nth-of-type(even)) {
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
Now, let's try something really fancy and exclude multiple items!
{{< hint info >}}
Remember that when you target multiple items in the list, the arguments you pass must be numbers and separated by comma.
{{</ hint >}}
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-except(1, 4, 5){
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(:nth-of-type(1)):not(:nth-of-type(4)):not(:nth-of-type(5)) {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example05 .list-item:not(:nth-of-type(1)):not(:nth-of-type(4)):not(:nth-of-type(5)) {
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

{{< highlightwrap class="example">}}
Let's exclude the items with class `exclude` on them.
{{< hint info >}}
When you pass arguments for `id` or `class` attributes of the items, don't forget to wrap your arguments with quotation. 
{{</ hint >}}

{{< highlight html >}}
<div class="list-wrapper">
    <div class="list-item exclude">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item exclude">06</div>
</div>
{{< /highlight >}}

{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-except(".exclude"){
            background-color: #5bc0bb;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(.exclude) {
    background-color: #5bc0bb;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example06 .list-item:not(.exclude) {
    background-color: #5bc0bb;
    color: white;
}
</style>
<div class="list-wrapper example06">
    <div class="list-item exclude">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item exclude">06</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now suppose you don't know the number of the items that will appear in the list, and that **you want to exclude the third item from the very end**. How can you achieve that? **The code below will target all the elements in the list except the second**.
{{< hint info >}}
You can pass negative values to exclude elements based on their position among a group of siblings, counting from the end.
{{</ hint >}}

{{< highlight scss >}}
.list-wrapper{
  .list-item{
    @include gls-except(-2){
      background-color: #5bc0bb;
      color: white;
    }
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(:nth-last-of-type(2)) {
  background-color: #5bc0bb;
  color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example07 .list-item:not(:nth-last-of-type(2)) {
  background-color: #5bc0bb;
  color: white;
}
</style>
<div class="list-wrapper example07">
    <div class="list-item exclude">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item exclude">06</div>
</div>
{{< /highlightwrap >}}
