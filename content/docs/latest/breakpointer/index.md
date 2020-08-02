---
title: "Breakpointer"
---

# Breakpointer

{{< mixin type="Mixin" name="breakpointer" >}}

**Breakpointer** Sass mixin is a handy small tool that points which breakpoint you are at so that you can write your styles for that specific breakpoint. 

{{< hint info >}}
**Tip:** This mixin works best with the predefined breakpoint values in the `_map-for-breakpoints.scss` file. Ok, let me put it this way. **If the breakpoint mixin is the knight, the breakpointer is its squire.**
{{< /hint >}}

{{< /mixin >}}

## Arguments

{{< arguments/table footnote="You can pass a declaration block to change its appearance cosmetically.">}}
    {{< arguments/row name="$selector" type="string" description="Help you to target one specific selector. Default it is targeting the `::before` pseudo-element of the `<body>` tag." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Call the mixin at the root level of your style sheet without passing any argument.
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
You can pass a CSS declaration block to customize the looking (as I did when I was developing the Gerillass' site itself).
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

{{< hint info >}}
**Important:** This mixin is for development mode only. So don't forget to comment out or remove the code before going any further for the production.
{{< /hint >}}