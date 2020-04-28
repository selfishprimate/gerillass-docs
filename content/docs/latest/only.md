# Only

{{< featured type="Mixin" name="only" >}}
This mixin helps you to filter elements that match based on their position among a group of siblings and apply your style rules to **only** those elements.
{{< hint info >}}
You can pass a string or number (or multiple numbers seperated by comma) values to target the items based on their index number, class or id attibutes.
{{< /hint >}}
{{< /featured >}}

## Arguments

{{< arguments/table footnote="When you want to fetch a given value by using custom property the name of the property must start with 'data-' prefix. For more please see the examples.">}}

    {{< arguments/row name="--" type="string" description="You can pass a content as a string or fetch the given value using custom property like `data-content`." >}}

    {{< arguments/row name="--" type="number" description="You can pass a content as a string or fetch the given value using custom property like `data-content`." >}}

{{< /arguments/table >}}

## Examples

Imagine that you have a group of items and you want to make some style changes only for some of them.

{{< highlight html >}}
<div class="list-wrapper">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlight >}}
{{< highlightwrap class="example">}}
Let's start with the first one!
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-only(first) {
            background-color: crimson;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:first-of-type {
    background-color: crimson;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example01 .list-item:first-of-type {
    background-color: crimson;
    color: white;
}
</style>
<div class="list-wrapper example01">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlightwrap >}}


{{< highlightwrap class="example">}}
Now, let's target the second item in the list.
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-only(2) {
            background-color: crimson;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:first-of-type {
    background-color: crimson;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example02 .list-item:nth-of-type(2) {
    background-color: crimson;
    color: white;
}
</style>
<div class="list-wrapper example02">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
You can make multiple selection as well.
{{< hint info >}}
Remember that when you make a multiple selection the arguments you pass must be numbers and separated by comma.
{{</ hint >}}
{{< highlight scss >}}
.list-wrapper{
    .list-item{
        @include gls-only(2, 4, 6) {
            background-color: crimson;
            color: white;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.list-wrapper .list-item:nth-of-type(2), 
.list-wrapper .list-item:nth-of-type(4), 
.list-wrapper .list-item:nth-of-type(6) {
    background-color: crimson;
    color: white;
}
{{< /highlight >}}
<style>
.list-wrapper.example03 .list-item:nth-of-type(2), 
.list-wrapper.example03 .list-item:nth-of-type(4), 
.list-wrapper.example03 .list-item:nth-of-type(6) {
    background-color: crimson;
    color: white;
}
</style>
<div class="list-wrapper example03">
    <div class="list-item">01</div>
    <div class="list-item">02</div>
    <div class="list-item">03</div>
    <div class="list-item">04</div>
    <div class="list-item">05</div>
    <div class="list-item">06</div>
</div>
{{< /highlightwrap >}}

