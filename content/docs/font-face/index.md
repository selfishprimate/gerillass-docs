---
title: "Font Face"
page_title: "Font Face Sass Mixin"
page_description: "The Font Face Sass mixin helps you generate a cross-browser compatible @font-face CSS at-rule in CSS and SCSS."
---

# Font Face

{{< mixin type="Mixin" name="font-face" >}}
The **Font Face** Sass mixin helps you generate a cross-browser compatible @font-face declaration.
{{< hint info >}}
**Important:** The mixin must be called at the root level of your stylesheet.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="To learn more about the **font-weight** property values, check out the [links](#related-articles) at the end of the article.">}}
  {{< arguments/row name="$font-family" type="string" description="Sets the name of the `font-family`." >}}
  {{< arguments/row name="$file-path" type="string" description="Sets the path and the name of the font file. The file name must be written without the extension." >}}
  {{< arguments/row name="$font-style" type="string" description="Sets the `font-style` property. The default value is `normal`. If there is an `italic` version of the font, you can set the value to `italic` or `oblique`." >}}
  {{< arguments/row name="$font-weight" type="number" description="Sets the weight of the font. The default value is `400`. Accepts `100`, `200`, `300`, `400`, `500`, `600`, `700`, `800`, and `900`." >}}
  {{< arguments/row name="$file-formats" type="string | list" description="Sets the font file formats you want to include. The default value is `eot woff2 woff ttf svg`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Let's call the mixin and pass values for the required arguments: `$font-family` and `$file-path`.
{{< highlight scss >}}
@include font-face("Fanwood Text", "fonts/fanwood-text/fanwood-text-regular");
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("fonts/fanwood-text/fanwood-text-regular.eot");
  src: url("fonts/fanwood-text/fanwood-text-regular.eot?#iefix") format("embedded-opentype"), 
       url("fonts/fanwood-text/fanwood-text-regular.woff2") format("woff2"), 
       url("fonts/fanwood-text/fanwood-text-regular.woff") format("woff"), 
       url("fonts/fanwood-text/fanwood-text-regular.ttf") format("truetype"), 
       url("fonts/fanwood-text/fanwood-text-regular.svg#FanwoodText") format("svg");
  font-style: normal;
  font-weight: 400;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's add the `italic` version of the family.
{{< highlight scss >}}
@include font-face("Fanwood Text", "fonts/fanwood-text/fanwood-text-regular", italic);
{{< /highlight >}}
{{< highlight css "linenos=table,hl_lines=10,linenostart=1" >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("../fonts/fanwood-text/fanwood-text-v9-latin-italic.eot");
  src: url("../fonts/fanwood-text/fanwood-text-v9-latin-italic.eot?#iefix") format("embedded-opentype"),
       url("../fonts/fanwood-text/fanwood-text-v9-latin-italic.woff2") format("woff2"), 
       url("../fonts/fanwood-text/fanwood-text-v9-latin-italic.woff") format("woff"), 
       url("../fonts/fanwood-text/fanwood-text-v9-latin-italic.ttf") format("truetype"), 
       url("../fonts/fanwood-text/fanwood-text-v9-latin-italic.svg#FanwoodText") format("svg");
  font-style: italic;
  font-weight: 400;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's add the `bold` version of the `Fanwood Text` font-family (if there is one) by passing `700` for the `$font-weight` argument.
{{< highlight scss >}}
@include font-face("Fanwood Text", "fonts/fanwood-text/fanwood-text-bold", 700);
{{< /highlight >}}
{{< highlight css "linenos=table,hl_lines=11,linenostart=1" >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("fonts/fanwood-text/fanwood-text-bold.eot");
  src: url("fonts/fanwood-text/fanwood-text-bold.eot?#iefix") format("embedded-opentype"), 
       url("fonts/fanwood-text/fanwood-text-bold.woff2") format("woff2"), 
       url("fonts/fanwood-text/fanwood-text-bold.woff") format("woff"), 
       url("fonts/fanwood-text/fanwood-text-bold.ttf") format("truetype"), 
       url("fonts/fanwood-text/fanwood-text-bold.svg#FanwoodText") format("svg");
  font-style: normal;
  font-weight: 700;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
If you pass values for both the `$font-style` and `$font-weight` arguments, the `$font-weight` value should always come last, unless you also pass a value for `$file-formats`.
{{< highlight scss >}}
@include font-face("Fanwood Text", "fonts/fanwood-text/fanwood-text-bold-italic", italic, 700);
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("fonts/fanwood-text/fanwood-text-bold-italic.eot");
  src: url("fonts/fanwood-text/fanwood-text-bold-italic.eot?#iefix") format("embedded-opentype"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.woff2") format("woff2"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.woff") format("woff"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.ttf") format("truetype"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.svg#FanwoodText") format("svg");
  font-style: italic;
  font-weight: 700;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< hint info >}}
Things get trickier when you want to pass a value for `$file-formats`. The examples below show the ways to do it.
{{< /hint >}}

{{< highlightwrap class="example">}}
Suppose you only have three file formats: `woff2`, `woff`, and `ttf`.
{{< highlight scss >}}
@include font-face("Fanwood Text", "fonts/fanwood-text/fanwood-text-regular", woff2 woff ttf);
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("fonts/fanwood-text/fanwood-text-regular.woff2") format("woff2"), 
       url("fonts/fanwood-text/fanwood-text-regular.woff") format("woff"), 
       url("fonts/fanwood-text/fanwood-text-regular.ttf") format("truetype");
  font-style: normal;
  font-weight: 400;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
If you want to pass values for all the arguments, the order must be `$font-family`, `$file-path`, `$font-style`, `$font-weight`, `$file-formats`, like in the example below.
{{< highlight scss >}}
@include font-face("Fanwood Text", "fonts/fanwood-text/fanwood-text-bold-italic", italic, 700, woff2 woff);
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("fonts/fanwood-text/fanwood-text-bold-italic.woff2") format("woff2"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.woff") format("woff");
  font-style: italic;
  font-weight: 700;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
If you are having trouble passing the arguments by position, try **named arguments**.
{{< hint info >}}
**Tip:** Do you know what is beautiful about named arguments? **They are order-independent**, which makes them very useful when it is hard to stick to the argument order.
{{< /hint >}}
{{< highlight scss >}}
@include font-face (
  $font-family: "Fanwood Text", 
  $file-path: "fonts/fanwood-text/fanwood-text-bold-italic",
  $font-style: italic, 
  $font-weight: 700,
  $file-formats: eot woff2 woff
);
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("fonts/fanwood-text/fanwood-text-bold-italic.eot");
  src: url("fonts/fanwood-text/fanwood-text-bold-italic.eot?#iefix") format("embedded-opentype"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.woff2") format("woff2"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.woff") format("woff");
  font-style: italic;
  font-weight: 700;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Try changing the order of the arguments. Whatever order you use, the result is the same.
{{< highlight scss >}}
@include font-face (
  $font-weight: 700,
  $font-style: italic,
  $file-formats: eot woff2 woff, 
  $font-family: "Fanwood Text",
  $file-path: "fonts/fanwood-text/fanwood-text-bold-italic",
);
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("fonts/fanwood-text/fanwood-text-bold-italic.eot");
  src: url("fonts/fanwood-text/fanwood-text-bold-italic.eot?#iefix") format("embedded-opentype"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.woff2") format("woff2"), 
       url("fonts/fanwood-text/fanwood-text-bold-italic.woff") format("woff");
  font-style: italic;
  font-weight: 700;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's use the `@content` directive to pass a content block into the mixin.
{{< highlight scss >}}
@include font-face ("Fanwood Text", "fonts/fanwood-text/fanwood-text-regular") {
  font-display: fallback;
}
{{< /highlight >}}
{{< highlight css "linenos=table,hl_lines=12,linenostart=1" >}}
//CSS Output
@font-face {
  font-family: "Fanwood Text";
  src: url("fonts/fanwood-text/fanwood-text-regular.eot");
  src: url("fonts/fanwood-text/fanwood-text-regular.eot?#iefix") format("embedded-opentype"),
       url("fonts/fanwood-text/fanwood-text-regular.woff2") format("woff2"),
       url("fonts/fanwood-text/fanwood-text-regular.woff") format("woff"),
       url("fonts/fanwood-text/fanwood-text-regular.ttf") format("truetype"),
       url("fonts/fanwood-text/fanwood-text-regular.svg#FanwoodText") format("svg");
  font-style: normal;
  font-weight: 400;
  font-display: fallback;
}
{{< /highlight >}}
{{< /highlightwrap >}}

If you don't have all the font varieties, or you have a font you want to convert into a **web font** (embeddable with @font-face), try **Font Squirrel**'s [Webfont Generator](https://www.fontsquirrel.com/tools/webfont-generator).

## Related Articles
* [Font Face](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face)  
* [Font Weight](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight)
* [Font Style](https://developer.mozilla.org/en-US/docs/Web/CSS/font-style)





