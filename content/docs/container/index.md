---
title: "Container"
page_title: "Container Sass Mixin"
page_description: "The Container Sass mixin marks an element as a query container, so container-query can ask about its width instead of the viewport's."
page_keywords: "CSS Container Queries, Sass Container Query, container-type, container-name, CSS inline-size, Component Level Responsiveness, Sass Container Mixin"
---

# Container

{{< mixin type="Mixin" name="container" >}}
A media query asks how wide the **viewport** is. That is the wrong question for a component that has to work in a sidebar, in a wide main column and in a grid cell on the same page. The **Container Sass mixin** marks an element as a query container, so [container-query](/docs/container-query/) can ask how wide **that element** is instead.

{{< hint danger >}}
**The rule that asks has to sit on a descendant.** An element is never matched by a `@container` rule that reads its own container. Measured in a browser: a 600px element carrying `container-type: inline-size` did **not** match `@container (min-width: 400px)`, while a child of it did. An element with no container ancestor at all matches nothing. Both fail silently, with no warning. The rule is simply never applied.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Give the container a name when a component sits inside another container and you need to say which one you mean.">}}
  {{< arguments/row name="$name (null)" type="string" description="Accepts a container name as a string, such as `\"card\"`, or `null` for an unnamed container." >}}
  {{< arguments/row name="$type (inline-size)" type="string" description="Accepts `inline-size`, `size`, or `normal`. `inline-size` queries the width only, which is what almost every layout needs." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
A named container. The name is what `container-query` targets when several containers are nested.
{{< highlight scss >}}
.card {
  @include container("card");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.card {
  container-type: inline-size;
  container-name: card;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Without a name. Queries with no `$name` resolve to the nearest container ancestor.
{{< highlight scss >}}
.panel {
  @include container;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.panel {
  container-type: inline-size;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Querying height as well as width costs more, because the element then has to be sized independently of its content. Reach for it only when you need it.
{{< highlight scss >}}
.panel {
  @include container(null, size);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.panel {
  container-type: size;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
A type that does not exist.
{{< highlight scss >}}
.card {
  @include container("card", sideways);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `sideways` is not a valid $type for `container`. Pass one of: inline-size, size, normal.
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
A name that is not a string.
{{< highlight scss >}}
.card {
  @include container(42);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `42` is not a valid $name for `container`. Pass a name as a string, such as `"card"`, or no name at all.
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Links
* [container-query](/docs/container-query/)
* [CSS container-type](https://developer.mozilla.org/en-US/docs/Web/CSS/container-type)
