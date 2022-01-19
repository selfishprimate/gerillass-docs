---
title: "Responsive Video"
---

# Responsive Video

{{< mixin type="Mixin" name="responsive-video" >}}
**Responsive Video** Sass mixin helps you create responsive containing elements with fixed aspect ratio that you define. This is especially useful when you embed videos from youtube or similar sources.

{{< hint info >}}
**Important:** Any direct child element you put inside the responsive video containers will be positioned `absolute` and take up as much space as the containing element. So, **do not put more than one direct child element** into the responsive video containers.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="The value you pass can be with or without the quotation marks." >}}
  {{< arguments/row name="$ratio" type="string, number" description="The aspect ratio of the video. Accepts either `number` or `string` type of values. The value must be formatted something like this: `16/9`, `4/3`, `1/1` based on the ratio of the video that you want to embed. Default ratio value is set to `16/9`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any argument. **Remember that the default `$ratio` value is set to `16/9`**.
{{< highlight html >}}
<div class="element">
  <iframe src="https://www.youtube.com/embed/JBc6JiRlsOU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include responsive-video;
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
<style>
.element.example01 {
  position: relative;
}
.element.example01::before {
  content: "";
  display: block;
  padding-top: 56.25%;
}
.element.example01 > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
</style>

<div class="element example01" style="margin-bottom: 1em;">
  <iframe src="https://www.youtube.com/embed/JBc6JiRlsOU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>  

Try to resize the browser screen to see the result.
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's **try with a video clip that has 4/3 aspect ratio** and pass the related value for `$ratio` argument. Comes from the loving voice of **Anna German**.
{{< highlight html >}}
<div class="element">
  <iframe src="https://www.youtube.com/embed/KYaCmvyK50Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include responsive-video(4/3);
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
<style>
.element.example02 {
  position: relative;
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
<div class="element example02">
<iframe src="https://www.youtube.com/embed/KYaCmvyK50Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's **pass a string value**.
{{< highlight html >}}
<div class="element">
  <iframe src="https://www.youtube.com/embed/fiyABGQnF5A" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include responsive-video("16/9");
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
<style>
.element.example03 {
  position: relative;
}
.element.example03::before {
  content: "";
  display: block;
  padding-top: 56.25%;
}
.element.example03 > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
</style>
<div class="element example03">
<iframe src="https://www.youtube.com/embed/fiyABGQnF5A" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's **pass a string value** and **use `colon` punctuation mark**. The result will be the same.
{{< highlight html >}}
<div class="element">
  <iframe src="https://www.youtube.com/embed/ymf7DZUeVow" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  @include responsive-video("16:9");
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
<style>
.element.example04 {
  position: relative;
}
.element.example04::before {
  content: "";
  display: block;
  padding-top: 56.25%;
}
.element.example04 > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
</style>
<div class="element example04">
<iframe src="https://www.youtube.com/embed/ymf7DZUeVow" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can **change the width value of the selected element** if you like, **the aspect ratio won't be collapsed**.
{{< highlight html >}}
<div class="element">
  <iframe src="https://www.youtube.com/embed/dK6Gvee-ri4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.element{
  width: 400px;
  @include responsive-video("16:9");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
  width: 400px;
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
<style>
.element.example05 {
  width: 400px;
  position: relative;
}
.element.example05::before {
  content: "";
  display: block;
  padding-top: 56.25%;
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
</style>
<div class="element example05">
<iframe src="https://www.youtube.com/embed/dK6Gvee-ri4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlightwrap >}}