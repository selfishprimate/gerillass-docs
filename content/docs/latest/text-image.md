---
title: "Text Image"
---

# Text Image

{{< mixin type="Mixin" name="text-image" >}}
**Text Image** Sass mixin helps you to clip the background image of a selected element to the shape of its foreground text. 
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="**Important:** Note that the URL of the image must be passed in quotation marks.">}}
    {{< arguments/row name="$image" type="string (quoted)" description="The URL of a clipping image." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in the selector and pass the URL of an image.
{{< highlight html >}}
<h2 class="element">Text Image is Awesome!</h2>
{{< /highlight >}}
{{< highlight scss >}}
.element{
    @include gls-text-image("https://i.picsum.photos/id/1015/6000/4000.jpg");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background-image: url("https://i.picsum.photos/id/1015/6000/4000.jpg");
    background-size: cover;
    background-position: center;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
}
{{< /highlight >}}
<h2 class="sandbox text" style="background-image: url('https://i.picsum.photos/id/1015/6000/4000.jpg');background-size: cover;background-position: center;-webkit-background-clip: text;-webkit-text-fill-color: transparent;background-clip: text;color: transparent;">Text Image is Awesome!</h2>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
The `$image` parameter is optional. This is very useful especially in the cases of loading images from the front face.
{{< highlight html >}}
<h2 class="element" style="background-image: url(https://i.picsum.photos/id/225/1500/979.jpg)">Text Image is Awesome!</h2>
{{< /highlight >}}
{{< highlight scss >}}
.element{
    @include gls-text-image;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background-size: cover;
    background-position: center;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
}
{{< /highlight >}}
<h2 class="sandbox text" style="background-image: url(https://i.picsum.photos/id/225/1500/979.jpg);background-size: cover;background-position: center;-webkit-background-clip: text;-webkit-text-fill-color: transparent;background-clip: text;color: transparent;">Text Image is Awesome!</h2>
{{< /highlightwrap >}}