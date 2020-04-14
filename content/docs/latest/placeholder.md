# Placeholder

{{< featured type="Mixin" name="placeholder" >}}
Suppose you have a containing element and a link inside of it. You want entire surface of this containing block to be clickable with this link. How can you do that?
{{< /featured >}}

## Examples

{{< highlight-wrapper class="example">}}
If no value is passed, the `::before` pseudo-element is targeted by default.
{{< highlight scss >}}
.element{
    @include gls-placeholder{
        color: red;
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::-webkit-input-placeholder {
    color: red;
}
.element::-moz-placeholder {
    color: red;
}
.element:-ms-input-placeholder {
    color: red;
}
.element:-moz-placeholder {
    color: red;
}
.element::placeholder {
    color: red;
}
{{< /highlight >}}