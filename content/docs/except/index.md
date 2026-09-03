---
title: "Except"
page_title: "Exclude Elements in the list with Except Sass Mixin"
page_description: "The Except Sass mixin helps you apply style changes to every element in a list except the ones you choose. It uses the :not() CSS pseudo-class."
---

# Except

{{< mixin type="Mixin" name="except" >}}
The **Except** Sass mixin helps you apply style changes to every element in a list except the ones you choose.
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

Let's say you have a list of items wrapped in a container, just like the example below. Now you want to apply some style changes to all of them, **except** for one or more.

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
    @include except(first){
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
    @include except(last){
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
    @include except(3){
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
Let's exclude the elements whose position is even (e.g. 2, 4, 6, and so on).
{{< highlight scss >}}
.list-wrapper{
  .list-item{
    @include except(even){
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
Remember that when you target multiple items in the list, the arguments you pass must be numbers separated by commas.
{{</ hint >}}
{{< highlight scss >}}
.list-wrapper{
  .list-item{
    @include except(1, 4, 5){
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
When you pass arguments for the `id` or `class` attributes of the items, don't forget to wrap your arguments in quotes. 
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
    @include except(".exclude"){
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
Now suppose you don't know how many items will appear in the list, and **you want to exclude the second item from the end**. How can you do that? It's easy!

{{< hint info >}}
**Information:** You can pass negative values to exclude elements based on their position among a group of siblings, counting from the end.
{{</ hint >}}

{{< highlight scss >}}
.list-wrapper{
  .list-item{
    @include except(-2){
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

{{< highlightwrap class="example">}}
Now let's pass multiple negative values.

{{< highlight scss >}}
.list-wrapper {
  .list-item {
    @include except(-2, -4) {
      background-color: #5bc0bb;
      color: white;
    }
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(:nth-last-of-type(2)):not(:nth-last-of-type(4)) {
  background-color: #5bc0bb;
  color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example08 .list-item:not(:nth-last-of-type(2)):not(:nth-last-of-type(4)) {
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

{{< highlightwrap class="example">}}
Now let's pass **positive and negative values together**.

{{< highlight scss >}}
.list-wrapper {
  .list-item {
    @include except(1, -1, -2) {
      background-color: #5bc0bb;
      color: white;
    }
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:not(:nth-of-type(1)):not(:nth-last-of-type(1)):not(:nth-last-of-type(2)) {
  background-color: #5bc0bb;
  color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example09 .list-item:not(:nth-of-type(1)):not(:nth-last-of-type(1)):not(:nth-last-of-type(2)) {
  background-color: #5bc0bb;
  color: white;
}
</style>
<div class="list-wrapper example09">
  <div class="list-item exclude">01</div>
  <div class="list-item">02</div>
  <div class="list-item">03</div>
  <div class="list-item">04</div>
  <div class="list-item">05</div>
  <div class="list-item exclude">06</div>
</div>
{{< /highlightwrap >}}
