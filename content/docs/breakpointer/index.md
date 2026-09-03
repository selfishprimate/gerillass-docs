---
title: "Breakpointer"
page_title: "Breakpointer Sass Mixin"
page_description: "The Breakpointer Sass mixin is a handy little tool that shows which breakpoint you are at, so you can write your styles for that specific device."
---

# Breakpointer

{{< mixin type="Mixin" name="breakpointer" >}}

The **Breakpointer Sass mixin** is a handy little tool that shows which breakpoint you are at, so you can write your styles for that specific screen size. 

{{< hint info >}}
This mixin has been applied to this page only, to show you how the **Breakpointer Sass mixin** works. You can see the result in the top right corner of your screen. **Please, resize the width of your browser to see which breakpoint you're at.**
{{< /hint >}}

{{< hint info >}}
**Tip:** This mixin works best with the predefined breakpoint values in the `_map-for-breakpoints.scss` file. OK, let me put it this way. **If the breakpoint mixin is the knight, the breakpointer is its squire.**
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="You can pass a declaration block to change its appearance cosmetically.">}}
    {{< arguments/row name="$selector" type="string" description="Helps you target one specific selector. By default it targets the `::before` pseudo-element of the `<body>` tag." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Call the mixin at the root level of your stylesheet without passing any arguments.
{{< highlight scss >}}
@include breakpointer;
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 0) {
  body::before {
    content: "xsmall";
  }
}
@media (min-width: 576px) {
  body::before {
    content: "small";
  }
}
@media (min-width: 768px) {
  body::before {
    content: "medium";
  }
}
@media (min-width: 992px) {
  body::before {
    content: "large";
  }
}
@media (min-width: 1200px) {
  body::before {
    content: "xlarge";
  }
}
{{< /highlight >}}
<figure class="highlight-figure">
  <img src="breakpointer_inspect.png" />
</figure>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can pass a CSS declaration block to customize how it looks (as I did when I was developing the Gerillass site itself).
{{< highlight scss >}}
@include breakpointer {
  position: fixed;
  top: 0;
  right: 0;
  color: white;
  padding: 5px 10px;
  z-index: 10;
}
{{< /highlight >}}

<p>You can change the appearance as you like. </p>

<figure class="highlight-figure">
  <img src="breakpointer_gerillass_02.png" />
</figure>

{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Well, good news! You can call the Breakpointer Sass mixin in a selector if you wish.
{{< highlight scss >}}
.element {
  @include breakpointer();
}
{{< /highlight >}}

{{< highlight css >}}
//CSS Output
@media (min-width: 0) {
  .element::before {
    content: "xsmall";
  }
}
@media (min-width: 576px) {
  .element::before {
    content: "small";
  }
}
@media (min-width: 768px) {
  .element::before {
    content: "medium";
  }
}
@media (min-width: 992px) {
  .element::before {
    content: "large";
  }
}
@media (min-width: 1200px) {
  .element::before {
    content: "xlarge";
  }
}
{{< /highlight >}}

{{< /highlightwrap >}}

{{< hint info >}}
**Important:** This mixin is for development only, so don't forget to comment out or remove the code before you go to production.
{{< /hint >}}