---
title: "Breakpoint"
---

# Breakpoint

{{< featured type="Mixin" name="breakpoint" >}}
**Breakpoint** Sass mixin helps you to write consistent media queries in Sass. Provides an easy to use one-line method.

{{< hint info >}}
**Tip:** There are predefined values for breakpoints in the `_map-for-breakpoints.scss` file based on Bootstraps' breakpoint values. **You can add more values here to expand the list or replace existing ones with yours**.
{{< /hint >}}

{{< /featured >}}

## Arguments

{{< arguments/table footnote="When you use `between` option you must pass two values for `width` and they must be seperated by space. For more see the [examples](#examples).">}}
    {{< arguments/row name="$mode" type="string" description="Sets the `width` media feature. Accepts `only`, `min`, `max` or `between` values." >}}
    {{< arguments/row name="$value" type="number (with unit)" description="The width value to which your styles will be applied." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin and pass a `width` value to it.  This code will apply styles only if your browser's viewport is equal to `320px`.
{{< highlight scss >}}
.element{
    @include gls-breakpoint(320px) {
        background-color: green;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (width: 320px) {
    .element {
        background-color: green;
    }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now, let's set the, `$mode` option to `min` and pass a pre-defined breakpoint value. If you are a **mobile-first** person you are going to use this one a lot!
{{< highlight scss >}}
.element{
    @include gls-breakpoint(min, medium) {
        background-color: green;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 768px) {
    .element {
        background-color: green;
    }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
For **desktop-first** arrangements set the `$mode` option to `max` and this time let's pass a custom `width` value.
{{< highlight scss >}}
.element{
    @include gls-breakpoint(max, 1024px) {
        background-color: green;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (max-width: 1024px) {
    .element {
        background-color: green;
    }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
We can set a range between two values ​​to apply our styles.
{{< hint info >}}
**Tip:** You can use **pre-defined** and **custom** values together if you like.
{{< /hint >}}
{{< highlight scss >}}
.element{
    @include gls-breakpoint(between, small 1200px) {
        background-color: green;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 576px) and (max-width: 1200px) {
    .element {
        background-color: green;
    }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
**Note that** when using the `between` mode with predefined values, the `max-width` value will always be extracted by one. **This setting prevents the styles ​​you apply from overlapping each other**. Examine the below code.
{{< highlight scss >}}
.element{
    @include gls-breakpoint(between, small medium) {
        background-color: green;
    };
    @include gls-breakpoint(between, medium large) {
        background-color: blue;
    };
    @include gls-breakpoint(between, large xlarge) {
        background-color: purple;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 576px) and (max-width: 767px) {
    .element {
        background-color: green;
    }
}
@media (min-width: 768px) and (max-width: 991px) {
    .element {
        background-color: blue;
    }
}
@media (min-width: 992px) and (max-width: 1199px) {
    .element {
        background-color: purple;
    }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Extracting by one is only for **pre-defined** values. When you work with custom values you don't have to worry about that!
{{< highlight scss >}}
.element{
    @include gls-breakpoint(between, small 1200px) {
        background-color: green;
    };
    @include gls-breakpoint(between, 1201px 1400px) {
        background-color: blue;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (min-width: 576px) and (max-width: 1200px) {
    .element {
        background-color: green;
    }
}
@media (min-width: 1201px) and (max-width: 1400px) {
    .element {
        background-color: blue;
    }
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
If you set the `mode` option to `only` you'll see that the result will be as same as the first example.
{{< highlight scss >}}
.element{
    @include gls-breakpoint(only, 1200px) {
        background-color: teal;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
@media (width: 1200px) {
    .element {
        background-color: teal;
    }
}
{{< /highlight >}}
{{< /highlightwrap >}}