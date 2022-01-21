---
title: "Sprite"
page_title: "Sprite Sass Mixin"
page_description: "Sprite Sass mixin helps you to apply background images to the selected element(s) by using CSS Sprite technique."
page_keywords: "CSS Sprite, Sass Sprite, CSS Sprite Technique, CSS Sprite Sheet Generator, CSS Sprite Tool, CSS Sprite Background Position, CSS Sprite and Image Maps"
---

# Sprite

{{< mixin type="Mixin" name="sprite" >}}
**Sprite** Sass mixin helps you to apply background images to the selected element(s) by using CSS Sprite technique.
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="To learn more about the `background-position` property values check out the [links](#related-articles) at the end of the page.">}}
  {{< arguments/row name="$image-url" type="string" description="The URL link of the sprite image. **Important:** Don't forget that the image link must be either absolute or relative to the generated CSS file." >}}
  {{< arguments/row name="$position" type="number | string" description="Sets the positioning of the `background-image`. **Multiple values must be seperated by space**." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
You can apply it to one single element and pass both `$image-url` and `$position` arguments by using one-line method.
{{< hint info >}}
**Important:** Don't forget to give a `width` and `height` values to the selected element. **It is very important to know the exact size of an image that you want to select from a sprite sheet**.
{{< /hint >}}
{{< highlight scss >}}
.sprite-element{
  @include sprite("../images/sprite.png", 0 0);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.sprite-element {
  display: inline-block;
  background-image: url("../images/sprite.png");
  background-position: 0 0;
  background-repeat: no-repeat;
}
{{< /highlight >}}
<style>
.sprite-element.single {
  width: 100px;
  height: 100px;
  display: inline-block;
  background-image: url("sprite.png");
  background-repeat: no-repeat;
}
</style>
<div class="sprite-elements">
  <div class="sprite-element single"></div>
</div>
{{< /highlightwrap >}}



{{< highlightwrap class="example">}}
Or you can apply it to multiple elements with different images selected from a single sprite sheet. **Well, suppose you have a markup like the one below, and you want to assign different background images to each element from a single sprite sheet**.
{{< highlight html >}}
<div class="sprite-element first"></div>
<div class="sprite-element second"></div>
<div class="sprite-element third"></div>
<div class="sprite-element fourth"></div>
{{< /highlight >}}

First let's call the mixin just to define the sprite image's url link and specify the `width` and `height` of the image that we're going to select.

{{< highlight scss >}}
.sprite-element{
  width: 100px;
  height: 100px;
  @include sprite("sprite.png");
}
{{< /highlight >}}

You can pass `width` and `height` values into the mixin as well!

{{< highlight scss >}}
.sprite-element{
  @include sprite("sprite.png") {
    width: 100px;
    height: 100px;
  };
}
{{< /highlight >}}

Then let's pass the positioning values for each of the elements separately using the secondary classes on them.

{{< highlight scss >}}
.sprite-element{
  @include sprite("sprite.png") {
    width: 100px;
    height: 100px;
  };
  &.first {
    @include sprite(0 0);
  }
  &.second {
    @include sprite(-100px 0)
  }
  &.third {
    @include sprite(-200px 0)
  }
  &.fourth {
    @include sprite(-300px 0)
  }
}
{{< /highlight >}}

Well, the result will be like this:
{{< highlight css >}}
//CSS Output
.sprite-element {
  width: 100px;
  height: 100px;
  display: inline-block;
  background-image: url("sprite.png");
  background-repeat: no-repeat;
}
.sprite-element.first {
  background-position: 0 0;
}
.sprite-element.second {
  background-position: -100px 0;
}
.sprite-element.third {
  background-position: -200px 0;
}
.sprite-element.fourth {
  background-position: -300px 0;
}
{{< /highlight >}}
<style>
.sprite-element {
  width: 100px;
  height: 100px;
  display: inline-block;
  background-image: url("sprite.png");
  background-repeat: no-repeat;
}
.sprite-element.first {
  background-position: 0 0;
}
.sprite-element.second {
  background-position: -100px 0;
}
.sprite-element.third {
  background-position: -200px 0;
}
.sprite-element.fourth {
  background-position: -300px 0;
}
</style>
<div class="sprite-elements">
  <div class="sprite-element first"></div>
  <div class="sprite-element second"></div>
  <div class="sprite-element third"></div>
  <div class="sprite-element fourth"></div>
</div>
{{< /highlightwrap >}}

Easy, isn't it?

## Related Articles
* [CSS Sprites](https://css-tricks.com/css-sprites/)
* [Background Position](https://developer.mozilla.org/en-US/docs/Web/CSS/background-position)