---
title: "Container Query"
page_title: "Container Query Sass Mixin"
page_description: "The Container Query Sass mixin writes a @container rule, taking the same argument shapes as the breakpoint mixin, so a component can respond to the width of its container instead of the viewport."
page_keywords: "CSS Container Query, Sass Container Query, @container, Component Queries, Container Query Breakpoints, CSS Container Query Example, Sass Container Query Mixin"
---

# Container Query

{{< mixin type="Mixin" name="container-query" >}}
The same component often has to work in a narrow sidebar and in a wide main column on the same page. A media query cannot tell those apart, because it only knows the viewport. The **Container Query Sass mixin** writes a `@container` rule, so the component responds to the width of its container instead.

It takes the same argument shapes as [breakpoint](/docs/breakpoint/), so the two read alike: a size, two sizes for a range, or `min`, `max`, `only` or `between` followed by a size. Sizes may be a key from `$map-for-breakpoints` or a raw length, and a raw length is the common case here, because a container is usually narrower than the viewport.

{{< hint danger >}}
**Put the container on an ancestor of the element you are styling.** This is the one thing to get right, and nothing tells you when you get it wrong. An element is never matched by a `@container` rule that reads its own container. Measured in a browser: a 600px element carrying `container-type: inline-size` did **not** match `@container (min-width: 400px)`, while a child of it did. An element with no container ancestor at all matches nothing. There is no warning in either case; the rule is just never applied.
{{< /hint >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="$name is passed as a keyword rather than by position, because `container-query(\"card\", \"medium\")` could not be told apart from `container-query(\"min\", \"medium\")`.">}}
  {{< arguments/row name="$params…" type="string, number" description="Accepts a size, two sizes for a range, or one of `min`, `max`, `only` or `between` followed by a size." >}}
  {{< arguments/row name="$name" type="string" description="Accepts a container name as a string, to query one named container rather than the nearest one. Pass it as a keyword, `$name: \"card\"`." >}}
{{< /arguments/table >}}

## Examples

The markup all of these assume: the container on the parent, the query on the child.

{{< highlightwrap >}}
{{< highlight html >}}
<div class="card">
  <h2 class="title">A title that grows once its card is wide enough</h2>
</div>
{{< /highlight >}}
{{< highlight scss >}}
.card {
  @include container("card");
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
From a width upwards, which is the one you will reach for most.
{{< highlight scss >}}
.title {
  @include container-query("min", 400px) {
    font-size: 2rem;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@container (min-width: 400px) {
  .title {
    font-size: 2rem;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Up to a width.
{{< highlight scss >}}
.title {
  @include container-query("max", 399px) {
    font-size: 1rem;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@container (max-width: 399px) {
  .title {
    font-size: 1rem;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
A range, written either with `between` or as two sizes. Both produce the same rule.
{{< highlight scss >}}
.title {
  @include container-query("between", 300px 500px) {
    color: red;
  }
}
.title {
  @include container-query(300px, 500px) {
    color: red;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@container (min-width: 300px) and (max-width: 500px) {
  .title {
    color: red;
  }
}
@container (min-width: 300px) and (max-width: 500px) {
  .title {
    color: red;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
A predefined breakpoint name works too, resolved through `$map-for-breakpoints`.
{{< highlight scss >}}
.title {
  @include container-query("min", "medium") {
    color: red;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@container (min-width: 768px) {
  .title {
    color: red;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Naming the container you mean. Without a name the query resolves to the nearest container ancestor, which is the wrong one as soon as containers are nested.
{{< highlight scss >}}
.title {
  @include container-query("min", 400px, $name: "card") {
    color: red;
  }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@container card (min-width: 400px) {
  .title {
    color: red;
  }
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

Arguments are checked, so a wrong value stops the build with a message instead of quietly producing the wrong CSS.

{{< highlightwrap >}}
Three sizes. A range takes two.
{{< highlight scss >}}
.title {
  @include container-query("min", 400px, 800px) {
    color: red;
  }
}
{{< /highlight >}}
{{< highlight text >}}
Error: `container-query` takes one or two arguments, and was given 3. Pass a size, two sizes for a range, or one of `min`, `max`, `only` or `between` followed by a size.
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
A name that is not a string.
{{< highlight scss >}}
.title {
  @include container-query("min", 400px, $name: 42) {
    color: red;
  }
}
{{< /highlight >}}
{{< highlight text >}}
Error: `42` is not a valid $name for `container-query`. Pass a container name as a string, such as `"card"`.
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Links
* [container](/docs/container/)
* [breakpoint](/docs/breakpoint/)
* [CSS container queries](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_containment/Container_queries)
