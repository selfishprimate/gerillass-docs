---
title: "Responsive Video"
page_title: "Responsive Video Sass Mixin"
page_description: "The Responsive Video Sass mixin helps you create responsive container elements with a fixed aspect ratio that you define. This is especially useful when you embed videos from YouTube or similar sources."
page_keywords: "CSS Responsive Video, YouTube Videos with CSS, Responsive Videos, Responsive YouTube Video with CSS, Responsive YouTube Video with Sass, Responsive YouTube Video with SCSS, Responsive Video CSS, Responsive Video Embed"
---

# Responsive Video

{{< mixin type="Mixin" name="responsive-video" >}}
The **Responsive Video Sass mixin** helps you create responsive container elements with a fixed aspect ratio that you define. This is especially useful when you embed videos from YouTube or similar sources.

{{< hint info >}}
**Important:** Any direct child element you put inside a responsive video container will be positioned `absolute` and take up as much space as the container itself. So **do not put more than one direct child element** into a responsive video container.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="The value you pass can be written with or without quotation marks." >}}
  {{< arguments/row name="$ratio" type="string, number" description="The aspect ratio of the video. Accepts either `number` or `string` values. Format the value like `16/9`, `4/3`, or `1/1`, based on the ratio of the video you want to embed. The default value is `16/9`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments. **Remember that the default `$ratio` value is `16/9`**.
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

Try resizing the browser window to see the result.
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's **try a video clip that has a 4/3 aspect ratio** and pass the matching value for the `$ratio` argument. This one comes from the loving voice of **Anna German**.
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
Now let's **pass a string value** and **use the colon punctuation mark**. The result will be the same.
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
You can **change the width value of the selected element** if you like, and **the aspect ratio will not collapse**.
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