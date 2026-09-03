---
title: "Ratio Box"
page_title: "Ratio Box Sass Mixin"
page_description: "The Ratio Box Sass mixin helps you create proportional CSS boxes based on the aspect ratio values you pass. It is especially useful when you apply the background-image CSS property to the selected element, because whatever the width of the element, the aspect ratio is always preserved."
---

# Ratio Box

{{< mixin type="Mixin" name="ratio-box" >}}
The **Ratio Box Sass mixin** helps you create **proportional CSS boxes** based on the aspect ratio values you pass. It is especially useful when you apply the background-image CSS property to the selected element, because **whatever the width of the element, the aspect ratio is always preserved**.

The **Ratio Box** mixin works on the same principles as the **Responsive Video** mixin, and the usage is the same too.

{{< hint info >}}
**Important:** Any direct child element you put inside the **ratio box container** will be **absolutely positioned** and take up as much space as the container itself. 
{{< /hint >}}

{{< hint danger >}}
**Danger:** Do not put more than one direct child element inside a ratio box container.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="The value you pass can be written with or without quotation marks." >}}
  {{< arguments/row name="$ratio" type="string, number" description="The aspect ratio of the selected item. Accepts either `number` or `string` values. You can pass any aspect ratio you want, in formats such as `16/9`, `4/3`, and `1/1`. The default value is `16/9`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments. **The default value is `16/9`**.
{{< highlight scss >}}
.element{
  @include ratio-box;
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.element {
  position: relative;
}
.element::before {
  content: "";
  display: block;
  padding-top: 56.25%;
}
.element > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
Now let's change the aspect ratio and try it with a real world example, using one more mixin from the library to apply a background image to the selected element.
{{< highlight scss >}}
.element{
  @include ratio-box(4/3);
  @include background-image("/images/backgrounds/06.jpg");
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.element {
  position: relative;
  background-image: url("/images/backgrounds/06.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
.element::before {
  content: "";
  display: block;
  padding-top: 75%;
}
.element > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
{{< /highlight >}}

<style>
.element {
  border-radius: 3px;
}
.element.example02 {
  position: relative;
  background-image: url("/images/backgrounds/06.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}

.element.example02::before {
  content: "";
  display: block;
  padding-top: 75%;
}
.element.example02 > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
</style>
<div class="element example02"></div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now **let's pass a string** value! I guarantee the result will be the same.
{{< highlight scss >}}
.element{
  @include ratio-box("4/3");
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.element {
  position: relative;
}
.element::before {
  content: "";
  display: block;
  padding-top: 75%;
}
.element > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can use the **`:`** sign to separate the two numbers instead of **`/`**.
{{< hint info >}}
**Important:** If you use the **colon sign** inside the argument, the entire value must always be wrapped in quotation marks, just like in the example below.
{{< /hint >}}
{{< highlight scss >}}
.element{
  @include ratio-box("16:9");
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.element {
  position: relative;
}
.element::before {
  content: "";
  display: block;
  padding-top: 56.25%;
}
.element > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try again with an unusual aspect ratio, give the selected element a `max-width` value, and put a direct child element inside it that contains some dummy text.
{{< hint info >}}
**Important:** If you use the **colon sign** inside the argument, the entire value must always be wrapped in quotation marks, just like in the example below.
{{< /hint >}}
{{< highlight html >}}
<div class="element">
  <span class="text">The passage experienced a surge in popularity during the 1960s when Letraset used it on their dry-transfer sheets.</span>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  max-width: 500px;
  background-color: crimson;
  @include ratio-box(16/6);
  .text {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1em;
    color: white;
  }
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.element {
  max-width: 500px;
  background-color: crimson;
  position: relative;
}
.element::before {
  content: "";
  display: block;
  padding-top: 37.5%;
}
.element > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
.element .text {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1em;
  color: white;
}
{{< /highlight >}}
<style>
.element.example05 {
  max-width: 500px;
  background-color: crimson;
  position: relative;
}
.element.example05::before {
  content: "";
  display: block;
  padding-top: 37.5%;
}
.element.example05 > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
.element.example05 .text {
  display: -webkit-box;
  display: flex;
  -webkit-box-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  align-items: center;
  padding: 1em;
  color: white;
}
</style>
<div class="element example05">
  <span class="text">The passage experienced a surge in popularity during the 1960s when Letraset used it on their dry-transfer sheets.</span>
</div>
{{< /highlightwrap >}}
