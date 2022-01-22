---
title: "Loadify"
page_title: "Loadify Sass Mixin"
page_description: "Loadify Sass mixin is a handy tool that can help you make a page element load with a smooth fade-in effect during the time of page loadings. It also allows you to create smooth image loading effects."
---

# Loadify

{{< mixin type="Mixin" name="loadify" >}}

**Loadify** Sass mixin is a handy tool that can help you make a page element load with a smooth fade-in effect during the time of page loadings.

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="The time value must be specified in either seconds (s) or milliseconds (ms). The value must be positive or zero and the unit is always required.">}}
    {{< arguments/row name="$mode" type="string" description="Accepts `init` value. This initializes the whole effects for the selected elements. **It must be called once at the root of your stylesheet document.**" >}}
    {{< arguments/row name="$delay" type="time" description="Specifies the amount of time a design element must wait before it starts appearing on the page. The default value is set to `0.2s`." >}}
    {{< arguments/row name="$duration" type="time" description="Sets the length of time that a page element takes to load. **This is the second argument and always must be at the end and cannot be used alone.** The deafult value is set to `0.5s`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap >}}

Ok. Let's call the Loadify mixin as an initializer first at the root level of your stylesheet and pass the `init` value as an argument. **This will generate some common style rules and the `loadify` animation itself**.

{{< hint info >}}
**Important:** Initializer must be called once at the root level of your stylesheet (**not in a selector**).
{{< /hint >}}

{{< highlight scss >}}
@include loadify(init);
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
@keyframes loadify {
  to {
    opacity: 1;
    visibility: visible;
    backface-visibility: visible;
  }
}
.loadify-static-rules {
  opacity: 0;
  visibility: hidden;
  backface-visibility: hidden;
  animation-name: loadify;
  animation-fill-mode: forwards;
}
{{< /highlight >}}

Now let's see some examples.

{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's see the animation on an image element. Call the Loadify mixin inside the element selector and **do not pass any argument** yet just to see the loading effect with the default timing values. 

**Now scroll to the image and refresh the page to see how smooth the image appears on the page.**

{{< hint info >}}
**Keep in mind!** You are totally free to give whatever selector name you want to the element.
{{< /hint >}}

{{< highlight scss >}}
.loadify-img {
  @include loadify();
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.loadify-static-rules, .loadify-img {
  opacity: 0;
  visibility: hidden;
  backface-visibility: hidden;
  animation-name: loadify;
  animation-fill-mode: forwards;
}
.loadify-img {
  animation-delay: 0.2s;
  animation-duration: 0.5s;
}
{{< /highlight >}}

<style>

.loadify-figure {
  position: relative;
}

.loadify-figure::before {
  content: "";
  display: block;
  padding-top: 66.66667%;
}

.loadify-figure > * {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

@keyframes loadify {
  to {
    opacity: 1;
    visibility: visible;
    backface-visibility: visible;
  }
}

.loadify-static-rules, .example-1 img {
  opacity: 0;
  visibility: hidden;
  backface-visibility: hidden;
  animation-name: loadify;
  animation-fill-mode: forwards;
}

.example-1 img {
  animation-delay: 0.2s;
  animation-duration: 0.5s;
}

</style>

<figure class="highlight-figure loadify-figure example-1">
  <img src="images/01.jpg" />
</figure>

{{< /highlightwrap >}}
