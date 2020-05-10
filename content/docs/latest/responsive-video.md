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
    {{< arguments/row name="$ratio" type="string, number" description="Accepts only one arguments. It can be `number` or `string` type. The value must be formatted something like this: `16/9`, `4/3`, `1/1` based on the ratio of the video that you want to embed. Default ratio value is set to `16/9`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Let try calling it without passing an argument. Remember that the default `$ratio` value is set to `16/9`.
{{< highlight html >}}
<div class="responsive-video">
    <iframe src="https://www.youtube.com/embed/JBc6JiRlsOU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.responsive-video{
    @include gls-responsive-video;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.responsive-video {
    position: relative;
    padding-top: 56.25%;
}
.responsive-video > * {
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
.responsive-video.example01 {
    position: relative;
    padding-top: 56.25%;
    margin-bottom: 16px;
    border-radius: 3px;
    overflow: hidden;
}
.responsive-video > * {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
}
</style>
<div class="responsive-video example01">
    <iframe src="https://www.youtube.com/embed/JBc6JiRlsOU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

Try to resize the browser screen to see the result.

{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's try with a video clip that has 4/3 aspect ratio and pass the related value for `$ratio` argument. Comes from the loving voice of **Anna German**.
{{< highlight html >}}
<div class="responsive-video">
    <iframe src="https://www.youtube.com/embed/KYaCmvyK50Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.responsive-video{
    @include gls-responsive-video(4/3);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.responsive-video {
    position: relative;
    padding-top: 75%;
}
.responsive-video > * {
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
.responsive-video.example02 {
    position: relative;
    padding-top: 75%;
    margin-bottom: 16px;
    border-radius: 3px;
    overflow: hidden;
}
</style>
<div class="responsive-video example02">
<iframe width="560" height="315" src="https://www.youtube.com/embed/KYaCmvyK50Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's pass a string value.
{{< highlight html >}}
<div class="responsive-video">
    <iframe src="https://www.youtube.com/embed/fiyABGQnF5A" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.responsive-video{
    @include gls-responsive-video("16/9");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.responsive-video {
    position: relative;
    padding-top: 56.25%;
}
.responsive-video > * {
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
.responsive-video.example03 {
    position: relative;
    padding-top: 56.25%;
    margin-bottom: 16px;
    border-radius: 3px;
    overflow: hidden;
}
</style>
<div class="responsive-video example03">
<iframe src="https://www.youtube.com/embed/fiyABGQnF5A" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
{{< /highlightwrap >}}