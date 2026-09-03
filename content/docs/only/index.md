---
title: "Only"
page_title: "Only Sass Mixin"
page_description: "The Only Sass mixin helps you target elements based on their position among siblings of the same type (tag name). This mixin uses the :first-of-type, :last-of-type, and :nth-of-type CSS pseudo-classes."
---

# Only

{{< mixin type="Mixin" name="only" >}}
The **Only** Sass mixin helps you filter elements based on their position among a group of siblings and apply your style rules to **only** those elements. This mixin uses `:first-of-type`, `:last-of-type`, and `:nth-of-type` CSS pseudo-classes.
{{< hint info >}}
You can pass a **string** value to target elements by their `id`, `class`, or `pseudo-class` selector. Or you can pass a **number** (or **multiple numbers** separated by commas) to target items by their index position in the list.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="**Important:** Passing multiple arguments only works with numeric values, and the values must be separated by commas.">}}
  {{< arguments/row name="--" type="string" description="The pseudo-class, class, or id selector. Accepts `first`, `last`, `odd`, `even`, and class or id selectors." >}}
  {{< arguments/row name="--" type="number" description="The index number of the element in the list. You can also make multiple selections." >}}
{{< /arguments/table >}}

## Examples

Suppose you have a group of items like the ones below, and you want to apply style changes to only some of them.

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
    @include only(first) {
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
    @include only(last) {
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
    @include only(2) {
      background-color: #5bc0bb;
      color: white;
    }
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:nth-of-type(2) {
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
Let's get the elements whose position is odd (e.g. 1, 3, 5, and so on).
{{< highlight scss >}}
.list-wrapper{
  .list-item{
    @include only(odd){
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
Remember that when you make a multiple selection, the arguments you pass must be numbers separated by commas.
{{</ hint >}}
{{< highlight scss >}}
.list-wrapper{
  .list-item{
    @include only(4, 5, 6) {
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

{{< highlightwrap class="example">}}
Now suppose you don't know how many items will appear in the list, and **you want to target only the third item from the end**. How can you do that? It's surprisingly easy!

{{< hint info >}}
**Information:** You can pass negative values to target elements based on their position among a group of siblings, counting from the end.
{{</ hint >}}

{{< highlight scss >}}
.list-wrapper {
  .list-item {
    @include only(-3) {
      background-color: #5bc0bb;
      color: white;
    }
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:nth-last-of-type(3) {
  background-color: #5bc0bb;
  color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example06 .list-item:nth-last-of-type(3) {
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
Now let's pass multiple negative values.
{{< highlight scss >}}
.list-wrapper {
  .list-item {
    @include only(-1, -2, -4) {
      background-color: #5bc0bb;
      color: white;
    }
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:nth-last-of-type(1), 
.list-wrapper .list-item:nth-last-of-type(2), 
.list-wrapper .list-item:nth-last-of-type(4) {
  background-color: #5bc0bb;
  color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example07 .list-item:nth-last-of-type(1), 
.list-wrapper.example07 .list-item:nth-last-of-type(2), 
.list-wrapper.example07 .list-item:nth-last-of-type(4) {
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

{{< highlightwrap class="example">}}
Now let's pass **positive and negative values together**.
{{< highlight scss >}}
.list-wrapper {
  .list-item {
    @include only(1, -2) {
      background-color: #5bc0bb;
      color: white;
    }
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:nth-of-type(1), 
.list-wrapper .list-item:nth-last-of-type(2) {
  background-color: #5bc0bb;
  color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example08 .list-item:nth-of-type(1),
.list-wrapper.example08 .list-item:nth-last-of-type(2) {
  background-color: #5bc0bb;
  color: white;
}
</style>
<div class="list-wrapper example08">
  <div class="list-item exclude">01</div>
  <div class="list-item">02</div>
  <div class="list-item">03</div>
  <div class="list-item">04</div>
  <div class="list-item">05</div>
  <div class="list-item exclude">06</div>
</div>
{{< /highlightwrap >}}


