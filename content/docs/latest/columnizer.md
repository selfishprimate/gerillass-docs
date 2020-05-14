---
title: "Columnizer"
---

# Columnizer

{{< mixin type="Mixin" name="columnizer" >}}
**Columnizer** Sass mixin helps you to **create evenly divided hypothetical columns** in a containing element, as many as the value you pass for the `$columns` argument. Thus, you can show all the children inside the parent element like they are lined up in a column. 

**Important:** Columnizer mixin **must be aplied to the parent** element to **align the children** inside of it!
{{< hint info >}}
**Tip:** This mixin is very useful when you want to create a **card-based design layouts**.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
    {{< arguments/row name="$columns" type="number" description="Sets the number of the hypothetical columns." >}}
    {{< arguments/row name="$gutter" type="number (with unit)" description="Sets the value of the space between the columns." >}}
    {{< arguments/row name="$fill" type="boolean" description="It is for orphans to fill the remaining gap at the end of the list. This argument is optional and **should always be at the end**. The default value is set to false." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap >}}
Suppose you have a group of items like in the example below and you want to make them look lined up in columns (**There are pre-defined style rules for items to show the differences more easily**).
{{< highlight html >}}
<div class="parent-element">
    <div class="item">01</div>
    <div class="item">02</div>
    <div class="item">03</div>
    <div class="item">04</div>
    <div class="item">05</div>
    <div class="item">06</div>
    <div class="item">07</div>
    <div class="item">08</div>
</div>
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's get cracking. Just call the mixin in the `.parent-element{}` selector and pass a value for the number of columns.
{{< highlight scss >}}
.parent-element{
    @include gls-columnizer(3);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
    display: flex;
    flex-wrap: wrap;
}
.parent-element > * {
    flex: 0 0 calc(100% / 3);
    margin-bottom: 0;
}
.parent-element > *:not(:last-child) {
    margin-right: 0;
}
{{< /highlight >}}

<style>
.parent-element.example01 {
  display: flex;
  flex-wrap: wrap;
}
.parent-element.example01 > * {
  flex: 0 0 calc(100% / 3);
  margin-bottom: 0;
}
.parent-element.example01 > *:not(:last-child) {
  margin-right: 0;
}
</style>
<div class="columnizer parent-element example01">
    <div class="item">01</div>
    <div class="item">02</div>
    <div class="item">03</div>
    <div class="item">04</div>
    <div class="item">05</div>
    <div class="item">06</div>
    <div class="item">07</div>
    <div class="item">08</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's pass a value for `$gutter` argument to separate every item from each other.
{{< highlight scss >}}
.parent-element{
    @include gls-columnizer(3, 20px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
    display: flex;
    flex-wrap: wrap;
}
.parent-element > * {
    flex: 0 0 calc((100% - (3 - 1) * 20px) / 3);
    margin-bottom: 20px;
}
.parent-element > *:not(:last-child) {
    margin-right: 20px;
}
.parent-element > *:nth-child(3n) {
    margin-right: 0;
}
{{< /highlight >}}

<style>
.parent-element.example02 {
  display: flex;
  flex-wrap: wrap;
}
.parent-element.example02 > * {
  flex: 0 0 calc((100% - (3 - 1) * 20px) / 3);
  margin-bottom: 20px;
}
.parent-element.example02 > *:not(:last-child) {
  margin-right: 20px;
}
.parent-element.example02 > *:nth-child(3n) {
  margin-right: 0;
}
</style>
<div class="columnizer parent-element example02">
    <div class="item">01</div>
    <div class="item">02</div>
    <div class="item">03</div>
    <div class="item">04</div>
    <div class="item">05</div>
    <div class="item">06</div>
    <div class="item">07</div>
    <div class="item">08</div>
</div>
{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
To make the orphans fill the gap let's pass `true` value at the end.
{{< highlight scss >}}
.parent-element{
    @include gls-columnizer(3, 20px, true);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
    display: flex;
    flex-wrap: wrap;
}
.parent-element > * {
    flex: 1 0 calc((100% - (3 - 1) * 20px) / 3);
    margin-bottom: 20px;
}
.parent-element > *:not(:last-child) {
    margin-right: 20px;
}
.parent-element > *:nth-child(3n) {
    margin-right: 0;
}
{{< /highlight >}}

<style>
.parent-element.example03 {
  display: flex;
  flex-wrap: wrap;
}
.parent-element.example03 > * {
  flex: 1 0 calc((100% - (3 - 1) * 20px) / 3);
  margin-bottom: 20px;
}
.parent-element.example03 > *:not(:last-child) {
  margin-right: 20px;
}
.parent-element.example03 > *:nth-child(3n) {
  margin-right: 0;
}
</style>
<div class="columnizer parent-element example03">
    <div class="item">01</div>
    <div class="item">02</div>
    <div class="item">03</div>
    <div class="item">04</div>
    <div class="item">05</div>
    <div class="item">06</div>
    <div class="item">07</div>
    <div class="item">08</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use either `$gutter` or `$fill` arguments optionallt. But remember, **the $fill argument should always be at the end**.
{{< highlight scss >}}
.parent-element{
    @include gls-columnizer(3, true);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
    display: flex;
    flex-wrap: wrap;
}
.parent-element > * {
    flex: 1 0 calc(100% / 3);
    margin-bottom: 0;
}
.parent-element > *:not(:last-child) {
    margin-right: 0;
}
{{< /highlight >}}

<style>
.parent-element.example04 {
  display: flex;
  flex-wrap: wrap;
}
.parent-element.example04 > * {
  flex: 1 0 calc(100% / 3);
  margin-bottom: 0;
}
.parent-element.example04 > *:not(:last-child) {
  margin-right: 0;
}
</style>
<div class="columnizer parent-element example04">
    <div class="item">01</div>
    <div class="item">02</div>
    <div class="item">03</div>
    <div class="item">04</div>
    <div class="item">05</div>
    <div class="item">06</div>
    <div class="item">07</div>
    <div class="item">08</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try it with the **breakpoint mixin** to show you how they these mixins work harmoniously together.
{{< highlight scss >}}
.parent-element{
    @include gls-columnizer(2, 10px, true);
    @include gls-breakpoint(min, large) {
        @include gls-columnizer(4, 20px, false);
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
    display: flex;
    flex-wrap: wrap;
}
.parent-element > * {
    flex: 1 0 calc((100% - (2 - 1) * 10px) / 2);
    margin-bottom: 10px;
}
.parent-element > *:not(:last-child) {
    margin-right: 10px;
}
.parent-element > *:nth-child(2n) {
    margin-right: 0;
}
@media (min-width: 992px) {
    .parent-element {
        display: flex;
        flex-wrap: wrap;
    }
    .parent-element > * {
        flex: 0 0 calc((100% - (4 - 1) * 20px) / 4);
        margin-bottom: 20px;
    }
    .parent-element > *:not(:last-child) {
        margin-right: 20px;
    }
    .parent-element > *:nth-child(4n) {
        margin-right: 0;
    }
}
{{< /highlight >}}

<style>
.parent-element.example05 {
  display: flex;
  flex-wrap: wrap;
}
.parent-element.example05 > * {
  flex: 1 0 calc((100% - (2 - 1) * 10px) / 2);
  margin-bottom: 10px;
}
.parent-element.example05 > *:not(:last-child) {
  margin-right: 10px;
}
.parent-element.example05 > *:nth-child(2n) {
  margin-right: 0;
}
@media (min-width: 992px) {
  .parent-element.example05 {
    display: flex;
    flex-wrap: wrap;
  }
  .parent-element.example05 > * {
    flex: 0 0 calc((100% - (4 - 1) * 20px) / 4);
    margin-bottom: 20px;
  }
  .parent-element.example05 > *:not(:last-child) {
    margin-right: 20px;
  }
  .parent-element.example05 > *:nth-child(4n) {
    margin-right: 0;
  }
}

</style>
<div class="columnizer parent-element example05">
    <div class="item">01</div>
    <div class="item">02</div>
    <div class="item">03</div>
    <div class="item">04</div>
    <div class="item">05</div>
    <div class="item">06</div>
    <div class="item">07</div>
</div>
{{< /highlightwrap >}}












<style>
.parent-element .item {
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #5bc0bb;
  font-weight: bold;
  color: #d8f7f5;
}
.parent-element .item:nth-of-type(even) {
  background-color: #d8f7f5;
  color: #5bc0bb;
}
</style>
