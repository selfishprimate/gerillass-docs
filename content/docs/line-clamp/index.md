---
title: "Line Clamp"
page_title: "Line Clamp Sass Mixin"
page_description: "The Line Clamp Sass mixin truncates text after a number of lines. It emits the five declarations the effect actually needs, because -webkit-line-clamp does nothing on its own."
page_keywords: "CSS Line Clamp, Sass Line Clamp, webkit-line-clamp, Multiline Truncate CSS, CSS Truncate Multiple Lines, Multiline Ellipsis CSS, Sass Text Truncation"
---

# Line Clamp

{{< mixin type="Mixin" name="line-clamp" >}}
[ellipsis](/docs/ellipsis/) truncates one line. The **Line Clamp Sass mixin** truncates several, cutting the text off after the number of lines you give it and ending with an ellipsis.

It emits **five declarations rather than one**, because `-webkit-line-clamp` does nothing on its own. Leave one of the others out and the text is not clamped at all, and nothing warns you.
{{< /mixin >}}

## What each declaration is doing

Every combination below was tested on a paragraph running to five lines, clamped to three.

<div class="table">
  <table>
    <thead>
      <tr>
        <th>What was applied</th>
        <th>Result</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="name">All three prefixed properties, plus <code>overflow</code></td>
        <td class="description">3 lines, with an ellipsis</td>
      </tr>
      <tr>
        <td class="name">Without <code>-webkit-box-orient: vertical</code></td>
        <td class="description">5 lines, no clamping, no warning</td>
      </tr>
      <tr>
        <td class="name">Without <code>display: -webkit-box</code></td>
        <td class="description">5 lines, the same</td>
      </tr>
      <tr>
        <td class="name">The unprefixed <code>line-clamp</code> on its own</td>
        <td class="description">5 lines. It is not Baseline yet</td>
      </tr>
      <tr>
        <td class="name">Without <code>overflow: hidden</code></td>
        <td class="description">The box is 3 lines, but the rest of the text spills out below it</td>
      </tr>
    </tbody>
  </table>
  <p class="footnote">* That last row is the one to watch for. Measuring the element's height reports three lines and looks correct; only looking at it shows the text escaping the box.</p>
</div>

The unprefixed `line-clamp` is emitted alongside the prefixed trio. It does nothing today, as the fourth row shows, and it costs one line to be right when it ships.

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$lines (3)" type="number | keyword" description="Accepts a whole number of lines, at least 1, or `none` to undo a clamp." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Clamp an excerpt to three lines.
{{< highlight scss >}}
.excerpt {
  @include line-clamp(3);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.excerpt {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  line-clamp: 3;
  overflow: hidden;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Two lines, for a card title that must not push the card taller.
{{< highlight scss >}}
.title {
  @include line-clamp(2);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.title {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  line-clamp: 2;
  overflow: hidden;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Without an argument the clamp is three lines.
{{< highlight scss >}}
.default {
  @include line-clamp;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.default {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  line-clamp: 3;
  overflow: hidden;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Pass `none` to undo a clamp, for instance when an excerpt expands on click.
{{< highlight scss >}}
.full {
  @include line-clamp(none);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.full {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: none;
  line-clamp: none;
  overflow: hidden;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## What it refuses

A clamp is a whole number of lines, so anything else stops the build.

{{< highlightwrap >}}
Zero lines.
{{< highlight scss >}}
.excerpt {
  @include line-clamp(0);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `0` is not a valid $lines for `line-clamp`. Pass a whole number of lines that is at least 1, or `none` to undo a clamp.
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap >}}
A length. Lines are counted, not measured.
{{< highlight scss >}}
.excerpt {
  @include line-clamp(3px);
}
{{< /highlight >}}
{{< highlight text >}}
Error: `3px` is not a valid $lines for `line-clamp`. Pass a whole number of lines, or `none` to undo a clamp.
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Links
* [ellipsis](/docs/ellipsis/)
* [-webkit-line-clamp](https://developer.mozilla.org/en-US/docs/Web/CSS/-webkit-line-clamp)
