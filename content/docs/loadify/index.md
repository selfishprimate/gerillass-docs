---
title: "Loadify"
page_title: "Loadify Sass Mixin"
page_description: "Loadify Sass mixin is a handy tool that helps you make a page element load with a smooth fade-in effect while the page is loading. It also allows you to create smooth image loading effects."
page_keywords: "Smooth Image Loading with Sass, Smooth Page Loading, Medium Image Loading, Bootstrap Lazy Load Images, CSS Image Loading, Sass Image Loading, Lazy Load Content, Smooth Content Loading, CSS Smooth Content Loading, Defer Image Loading"
css: css/styles.css
---

# Loadify

{{< mixin type="Mixin" name="loadify" >}}

The The **Loadify Sass mixin** is a handy tool that helps you make a page element load with a smooth fade-in effect while the page is loading.

{{< hint info >}}
**Reduced motion is handled for you.** Under `prefers-reduced-motion: reduce` the end state is applied directly and no animation runs, so the content is simply there.

Note that **switching the animation off would not have worked.** The element starts at `opacity: 0` with `visibility: hidden`, and the animation is the thing that reveals it. Turning the animation off and doing nothing else would have left the content invisible for good. That is why the mixin sets the end state instead, and only then sets `animation: none`.
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="The time value must be given in either seconds (s) or milliseconds (ms). The value must be zero or positive, and the unit is always required.">}}
    {{< arguments/row name="$mode" type="string" description="Accepts `init` value. This initializes the whole effects for the selected elements. **It must be called once at the root of your stylesheet document.**" >}}
    {{< arguments/row name="$delay" type="time" description="Specifies the amount of time a design element must wait before it starts appearing on the page. The default value is set to `0.2s`." >}}
    {{< arguments/row name="$duration" type="time" description="Sets the length of time a page element takes to load. **This is the second argument. It must always come last and cannot be used on its own.** The default value is `0.5s`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap >}}

Let's start by calling the Loadify mixin as an initializer at the root level of your stylesheet, and pass the `init` value as an argument. **This will generate the `loadify` animation itself**.

{{< hint info >}}
**Tip:** When you call the mixin at the root of your stylesheet to initialize the effect, you can either pass the `init` argument or leave it blank.
{{< /hint >}}

{{< hint info >}}
**Important:** The initializer must be called once at the root level of your stylesheet (**not inside a selector**).
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
{{< /highlight >}}

Now let's see some examples.

{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Let's see the animation on an image element. Call the Loadify mixin inside the element's selector and **do not pass any arguments** yet, just to see the loading effect with the default timing values. 

**Now scroll to the image and refresh the page to see how smooth the image appears on the page.**

{{< hint info >}}
**Keep in mind!** You are free to give the element any selector name you want.
{{< /hint >}}

{{< highlight scss >}}
.loadify-img {
  @include loadify();
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.loadify-img {
  opacity: 0;
  visibility: hidden;
  backface-visibility: hidden;
  animation-name: loadify;
  animation-fill-mode: forwards;
}
@media (prefers-reduced-motion: reduce) {
  .loadify-img {
    opacity: 1;
    visibility: visible;
    backface-visibility: visible;
    animation: none;
  }
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

{{< highlightwrap class="example">}}
Let's dive a bit deeper to understand exactly what this handy tool can do.

Suppose you have a group of items like the ones below, and you want them to appear smoothly as the page loads.

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

{{< hint info >}}
**Keep in mind!** You must call the `loadify` mixin once at the root of your stylesheet as an initializer.
{{< /hint >}}

{{< highlight scss >}}
.parent-element {
  .item {
    @include loadify();
  }
}
{{< /highlight >}}

{{< hint info >}}
**Important!** When you call the mixin inside a selector without passing any arguments, it works differently, as you can see in the example below. Here, the `item` selector takes the default `animation-delay` and `animation-duration` values.
{{< /hint >}}

**Now scroll to the elements and refresh the page to see how smooth the elements appear on the page.**

{{< highlight css >}}
//CSS Output
.parent-element .item {
  opacity: 0;
  visibility: hidden;
  backface-visibility: hidden;
  animation-name: loadify;
  animation-fill-mode: forwards;
}
@media (prefers-reduced-motion: reduce) {
  .parent-element .item {
    opacity: 1;
    visibility: visible;
    backface-visibility: visible;
    animation: none;
  }
}

.parent-element .item {
  animation-delay: 0.2s;
  animation-duration: 0.5s;
}
{{< /highlight >}}

<div class="parent-element example-02">
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
Now let's pass `1s` as a custom value for the `animation-delay` CSS property, to set how long the selected element waits before it starts to appear.

**Refresh the page to see the effect.**

{{< highlight scss >}}
.parent-element {
  .item {
    @include loadify(1s);
  }
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.parent-element .item {
  opacity: 0;
  visibility: hidden;
  backface-visibility: hidden;
  animation-name: loadify;
  animation-fill-mode: forwards;
}
@media (prefers-reduced-motion: reduce) {
  .parent-element .item {
    opacity: 1;
    visibility: visible;
    backface-visibility: visible;
    animation: none;
  }
}

.parent-element .item {
  animation-delay: 1s;
  animation-duration: 0.5s;
}
{{< /highlight >}}

<div class="parent-element example-03">
  <div class="item">01</div>
  <div class="item">02</div>
  <div class="item">03</div>
  <div class="item">04</div>
  <div class="item">05</div>
  <div class="item">06</div>
  <div class="item">07</div>
  <div class="item">08</div>
</div>

It's getting more interesting, isn't it?

{{< /highlightwrap >}}

{{< highlightwrap class="example">}}

Now we are going to try a fantastic example to see how the Gerillass Sass library can ease your frontend development, and how well it works when you combine two or more mixins.

We will use the `only` mixin to select items in the list based on their index positions, and then call the `loadify` mixin inside each of those selectors to make the elements appear at different times (with different delay and duration values).

**Scroll to the bottom of this example and refresh the page to see the effect.**

{{< highlight scss >}}
.parent-element {
  .item {
    @include only(1) {
      @include loadify(0.2s);
    }
    @include only(2) {
      @include loadify(0.4s);
    }
    @include only(3) {
      @include loadify(0.6s);
    }
    @include only(4) {
      @include loadify(0.8s);
    }
    @include only(5) {
      @include loadify(0.1s);
    }
    @include only(6) {
      @include loadify(1.2s);
    }
    @include only(7) {
      @include loadify(1.4s);
    }
    @include only(8) {
      @include loadify(1.6s);
    }
  }
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.parent-element .item:nth-of-type(8), .parent-element .item:nth-of-type(7), .parent-element .item:nth-of-type(6), .parent-element .item:nth-of-type(5), .parent-element .item:nth-of-type(4), .parent-element .item:nth-of-type(3), .parent-element .item:nth-of-type(2), .parent-element .item:nth-of-type(1) {
  opacity: 0;
  visibility: hidden;
  backface-visibility: hidden;
  animation-name: loadify;
  animation-fill-mode: forwards;
}
@media (prefers-reduced-motion: reduce) {
  .parent-element .item:nth-of-type(8), .parent-element .item:nth-of-type(7), .parent-element .item:nth-of-type(6), .parent-element .item:nth-of-type(5), .parent-element .item:nth-of-type(4), .parent-element .item:nth-of-type(3), .parent-element .item:nth-of-type(2), .parent-element .item:nth-of-type(1) {
    opacity: 1;
    visibility: visible;
    backface-visibility: visible;
    animation: none;
  }
}

.parent-element .item:nth-of-type(1) {
  animation-delay: 0.2s;
  animation-duration: 0.5s;
}
.parent-element .item:nth-of-type(2) {
  animation-delay: 0.4s;
  animation-duration: 0.5s;
}
.parent-element .item:nth-of-type(3) {
  animation-delay: 0.6s;
  animation-duration: 0.5s;
}
.parent-element .item:nth-of-type(4) {
  animation-delay: 0.8s;
  animation-duration: 0.5s;
}
.parent-element .item:nth-of-type(5) {
  animation-delay: 0.1s;
  animation-duration: 0.5s;
}
.parent-element .item:nth-of-type(6) {
  animation-delay: 1.2s;
  animation-duration: 0.5s;
}
.parent-element .item:nth-of-type(7) {
  animation-delay: 1.4s;
  animation-duration: 0.5s;
}
.parent-element .item:nth-of-type(8) {
  animation-delay: 1.6s;
  animation-duration: 0.5s;
}
{{< /highlight >}}

<div class="parent-element example-04">
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
Now let's try another sexy example. This time we are going to **change the display order of the boxes (we will be using a diagonal pattern)** and **pass a value for the second argument to control the value of the `animation-duration` CSS property**.

The display order will be as follows: "**1**", "**6**", "**3**", "**8**", "**5**", "**2**", "**7**", "**4**" 

**Scroll to the bottom of this example and refresh the page to see the effect.**

{{< highlight scss >}}
.parent-element {
  .item {
    @include only(1) {
      @include loadify(0.2s, 0.5s);
    }
    @include only(2) {
      @include loadify(1.2s, 3s);
    }
    @include only(3) {
      @include loadify(0.6s, 1.5s);
    }
    @include only(4) {
      @include loadify(1.6s, 4s);
    }
    @include only(5) {
      @include loadify(1s, 2.5s);
    }
    @include only(6) {
      @include loadify(0.4s, 1s);
    }
    @include only(7) {
      @include loadify(1.4s, 3.5s);
    }
    @include only(8) {
      @include loadify(0.8s, 2s);
    }
  }
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
.parent-element .item:nth-of-type(8), .parent-element .item:nth-of-type(7), .parent-element .item:nth-of-type(6), .parent-element .item:nth-of-type(5), .parent-element .item:nth-of-type(4), .parent-element .item:nth-of-type(3), .parent-element .item:nth-of-type(2), .parent-element .item:nth-of-type(1) {
  opacity: 0;
  visibility: hidden;
  backface-visibility: hidden;
  animation-name: loadify;
  animation-fill-mode: forwards;
}
@media (prefers-reduced-motion: reduce) {
  .parent-element .item:nth-of-type(8), .parent-element .item:nth-of-type(7), .parent-element .item:nth-of-type(6), .parent-element .item:nth-of-type(5), .parent-element .item:nth-of-type(4), .parent-element .item:nth-of-type(3), .parent-element .item:nth-of-type(2), .parent-element .item:nth-of-type(1) {
    opacity: 1;
    visibility: visible;
    backface-visibility: visible;
    animation: none;
  }
}

.parent-element .item:nth-of-type(1) {
  animation-delay: 0.2s;
  animation-duration: 0.5s;
}
.parent-element .item:nth-of-type(2) {
  animation-delay: 1.2s;
  animation-duration: 3s;
}
.parent-element .item:nth-of-type(3) {
  animation-delay: 0.6s;
  animation-duration: 1.5s;
}
.parent-element .item:nth-of-type(4) {
  animation-delay: 1.6s;
  animation-duration: 4s;
}
.parent-element .item:nth-of-type(5) {
  animation-delay: 1s;
  animation-duration: 2.5s;
}
.parent-element .item:nth-of-type(6) {
  animation-delay: 0.4s;
  animation-duration: 1s;
}
.parent-element .item:nth-of-type(7) {
  animation-delay: 1.4s;
  animation-duration: 3.5s;
}
.parent-element .item:nth-of-type(8) {
  animation-delay: 0.8s;
  animation-duration: 2s;
}
{{< /highlight >}}

<div class="parent-element example-05">
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