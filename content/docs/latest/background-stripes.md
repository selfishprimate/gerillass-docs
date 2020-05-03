---
title: "Background Stripes"
---

# Background Stripes

{{< featured type="Mixin" name="background-stripes" >}}
This mixin allows you to create stylish and colorful background stripes.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="Multiple color values must be space-separated (e.g. $color: red blue green).">}}
    {{< arguments/row name="$color" type="list" description="The color(s) of the stripes. The default there is only one color and is set to opaque black. Accepts one or more color values to create multiple color-stops." >}}
    {{< arguments/row name="$thickness" type="number<br/>(with unit)" description="The thickness of the stripes. The default thickness value is 1em." >}}
    {{< arguments/row name="$rotation" type="number</br>(with deg unit)" description="The rotation of the stripes. The default value is set to `-45deg`. This option allows you to create diagonal or straight stripes very easily." >}}
    {{< arguments/row name="$image" type="string<br/>(quoted)" description="Accepts a URL of an image. This option helps you to add an image underneath the stripes to create more stylish design elements." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin without passing any arguments.
{{< highlight scss >}}
.element{
    @include gls-background-stripes();
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background-image: repeating-linear-gradient(
        -45deg, 
        rgba(0, 0, 0, 0.1) 0, 
        rgba(0, 0, 0, 0.1) 1em, 
        transparent 1em, 
        transparent 2em
    );
}
{{< /highlight >}}
{{< sandbox class="small" >}}
background-image: repeating-linear-gradient(-45deg, rgba(0, 0, 0, 0.1) 0, rgba(0, 0, 0, 0.1) 1em, transparent 1em, transparent 2em);
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's pass a `$color` value to it!
{{< highlight scss >}}
.element{
    @include gls-background-stripes(
        $color: pink
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background-image: repeating-linear-gradient(
        -45deg, 
        pink 0, 
        pink 1em, 
        transparent 1em, 
        transparent 2em
    );
}
{{< /highlight >}}
{{< sandbox class="small" >}}
background-image: repeating-linear-gradient(-45deg, pink 0, pink 1em, transparent 1em, transparent 2em);
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's add more colors and change the `$thickness` and `$rotation` values. **Important:** Don't forget that the multiple color values must be seperated by space!
{{< highlight scss >}}
.element{
    @include gls-background-stripes(
        $color: #FFD393 #FF974F #F54F29,
        $thickness: 3em,
        $rotation: 90deg
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background-image: repeating-linear-gradient(
        90deg, 
        #FFD393 0em, 
        #FFD393 3em, 
        #FF974F 3em, 
        #FF974F 6em, 
        #F54F29 6em, 
        #F54F29 9em
    );
}
{{< /highlight >}}
{{< sandbox class="small" >}}
background-image: repeating-linear-gradient(90deg, #FFD393 0em, #FFD393 3em, #FF974F 3em, #FF974F 6em, #F54F29 6em, #F54F29 9em);
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Add an image to make your design look more alive! **Just do not forget to use quotes when you pass the URL of an image.**
{{< highlight scss >}}
.element{
    @include gls-background-stripes(
        $color: rgba(blue, 0.4),
        $thickness: 3px,
        $rotation: 45deg,
        $image: "https://i.picsum.photos/id/1069/3500/2333.jpg"
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background-image: repeating-linear-gradient(
        45deg, 
        rgba(0, 0, 255, 0.4) 0, 
        rgba(0, 0, 255, 0.4) 3px, 
        transparent 3px, transparent 6px
    ), url("https://i.picsum.photos/id/1069/3500/2333.jpg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
{{< /highlight >}}
{{< sandbox class="xlarge" >}}
background-image: repeating-linear-gradient(45deg, rgba(0, 0, 255, 0.4) 0, rgba(0, 0, 255, 0.4) 3px, transparent 3px, transparent 6px), url('https://i.picsum.photos/id/1069/3500/2333.jpg');background-position: center;background-repeat: no-repeat;background-size: cover;
{{< /sandbox >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can create an old fashioned tv screen effect as well.
{{< highlight scss >}}
.element{
    @include gls-background-stripes(
        $color: black,
        $thickness: 1px,
        $rotation: 180deg,
        $image: "https://i.picsum.photos/id/528/4000/3000.jpg"
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    background-image: repeating-linear-gradient(
        180deg, 
        black 0, 
        black 1px, 
        transparent 1px, 
        transparent 2px
    ), url("https://i.picsum.photos/id/528/4000/3000.jpg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
{{< /highlight >}}

{{< sandbox class="xlarge" >}}
background-image: repeating-linear-gradient(180deg, black 0, black 1px, transparent 1px, transparent 2px), url(https://i.picsum.photos/id/528/4000/3000.jpg);background-position: center;background-repeat: no-repeat;background-size: cover;
{{< /sandbox >}}

Just play with the values of the given arguments to create more interesting things. **Use your imagination!**
{{< /highlightwrap >}}





