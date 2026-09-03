---
title: "Columnizer"
page_title: "Columnizer Sass Mixin"
page_description: "The Columnizer Sass mixin helps you create beautiful, responsive, card-based design layouts in CSS and Sass."
---

# Columnizer

{{< mixin type="Mixin" name="columnizer" >}}
The **Columnizer** Sass mixin helps you **create evenly divided hypothetical columns** inside a container element, as many as the value you pass for the `$columns` argument. This lets you show all the children of the parent element as if they were lined up in columns. 

**Important:** The Columnizer mixin **must be applied to the parent** element to **align the children** inside it!
{{< hint info >}}
**Tip:** This mixin is very useful when you want to create **card-based design layouts**.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$columns" type="number" description="Sets the number of the hypothetical columns." >}}
  {{< arguments/row name="$gutter" type="number (with unit)" description="Sets the value of the space between the columns." >}}
  {{< arguments/row name="$fill" type="boolean" description="Lets the orphans fill the remaining gap at the end of the list. This argument is optional and **should always come last**. The default value is `false`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap >}}
Suppose you have a group of items like the ones below, and you want to make them look like they are lined up in columns. (**The items have predefined style rules so the differences are easier to see.**)
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
Now let's get cracking. Just call the mixin inside the `.parent-element{}` selector and pass a value for the number of columns.
{{< highlight scss >}}
.parent-element{
  @include columnizer(3);
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
Let's pass a value for the `$gutter` argument to put space between the items.
{{< highlight scss >}}
.parent-element{
  @include columnizer(3, 20px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
  display: flex;
  flex-wrap: wrap;
}
.parent-element > * {
  flex-grow: 0;
  flex-shrink: 0;
  flex-basis: calc((100% - (3 - 1) * 20px) / 3);
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
To make the orphans fill the gap, let's pass the `true` value at the end.
{{< highlight scss >}}
.parent-element{
  @include columnizer(3, 20px, true);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
  display: flex;
  flex-wrap: wrap;
}
.parent-element > * {
  flex-grow: 1;
  flex-shrink: 0;
  flex-basis: calc((100% - (3 - 1) * 20px) / 3);
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
You can use either the `$gutter` or the `$fill` argument optionally. But remember, **the `$fill` argument should always come last**.
{{< highlight scss >}}
.parent-element{
  @include columnizer(3, true);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.parent-element {
  display: flex;
  flex-wrap: wrap;
}
.parent-element > * {
  flex-grow: 1;
  flex-shrink: 0;
  flex-basis: calc(100% / 3);
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
Now let's try it with the **breakpoint mixin** to show you how these mixins work harmoniously together.
{{< highlight scss >}}
.parent-element{
  @include columnizer(2, 10px, true);
  @include breakpoint(min, large) {
    @include columnizer(4, 20px, false);
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
  flex-grow: 1;
  flex-shrink: 0;
  flex-basis: calc((100% - (2 - 1) * 10px) / 2);
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
    flex-grow: 0;
    flex-shrink: 0;
    flex-basis: calc((100% - (4 - 1) * 20px) / 4);
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
