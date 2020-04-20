# Clearfix

{{< featured type="Mixin" name="clearfix" >}}
This mixin helps you to clear floats to prevent broken layouts and must be applied to the parent element.
{{< /featured >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin in an element to truncate the text inside of it.
{{< highlight scss >}}
.element{
    @include gls-clearfix;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element::after {
    content: "";
    display: block;
    clear: both;
}
{{< /highlight >}}
{{< /highlightwrap >}}

