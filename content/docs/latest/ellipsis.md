# Ellipsis

{{< featured type="Mixin" name="ellipsis" >}}
This mixin helps you to truncate a text and adds an **ellipsis** at the end of it based on the given `$width` value.
{{< /featured >}}

## Arguments

{{< arguments/table >}}
    {{< arguments/row name="$width (100%)" type="number <br/>(with unit)" description="The `max-width` of the selected element before beign truncated." >}}
    {{< arguments/row name="$display (inline-block)" type="string" description="Sets the value of the `display` property of the selected element(s) to `inline-block`." >}}
{{< /arguments/table >}}

## Examples

{{< highlight-wrapper class="example">}}
Simply call the mixin in an element to truncate the text inside of it.
{{< highlight scss >}}
.element{
    @include gls-ellipsis;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    display: inline-block;
    max-width: 100%;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    word-wrap: normal;
}
{{< /highlight >}}
{{< /highlight-wrapper >}}

{{< highlight-wrapper class="example">}}
Change the `$width` or `$display` values of the selected element(s) if you need to.
{{< highlight scss >}}
.element{
    @include gls-ellipsis(
        $width: 200px,
        $display: block
    );
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    display: block;
    max-width: 200px;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    word-wrap: normal;
}
{{< /highlight >}}
{{< /highlight-wrapper >}}
