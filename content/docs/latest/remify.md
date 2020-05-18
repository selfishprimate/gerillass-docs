---
title: "Remify"
---

# Remify

{{< function type="Function" name="remify" >}}
**Remify** function helps you to convert the `pixel` values to `rem`. 
{{< hint info >}}
**Tip:** It's especially useful when you work with rem units and having hard times to calculate how many rems that a pixel value you pass.
{{< /hint >}}
{{< /function >}}
## Arguments

{{< arguments/table >}}
    {{< arguments/row name="$value" type="number (with unit)" description="The pixel value that you want it to be converted to `rem`." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the function and pass a `pixel` value to it!
{{< highlight scss >}}
.element {
    font-size: __remify(30px);
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element {
    font-size: 1.875rem;
}
{{< /highlight >}}
{{< /highlightwrap >}}
