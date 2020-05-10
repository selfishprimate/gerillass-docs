---
title: "All Text Inputs"
---

# All Text Inputs

{{< featured type="Mixin" name="all-text-inputs" >}}
**All Text Inputs** Sass mixin helps you to target all the text-based HTML input elements in the DOM, thus you can easily apply your style rules.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="You can call the mixin either at the root level of your style sheet to target all the text-based input elements in the DOM or call it in a selector to target only some particular elements as children of the given selector.">}}
    {{< arguments/row name="$pseudo" type="string" description="It helps you to target pseudo classes of the selected text-based input elements. Accepts `hover`, `focus`, `active`, `invalid`, `required`, `disabled` values." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin at the root level of your style sheet **to target all the text-based input elements**.
{{< highlight scss >}}
@include gls-all-text-inputs {
    background-color: #e6e6e6;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
[type='color'], 
[type='date'], 
[type='datetime'], 
[type='datetime-local'], 
[type='email'], 
[type='month'], 
[type='number'], 
[type='password'], 
[type='search'], 
[type='tel'], 
[type='text'], 
[type='time'], 
[type='url'], 
[type='week'], 
input:not([type]), 
textarea {
    background-color: #e6e6e6;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's style the **hover state** of the inputs.
{{< highlight scss >}}
@include gls-all-text-inputs(hover) {
    background-color: orange;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
[type='color']:hover, 
[type='date']:hover, 
[type='datetime']:hover, 
[type='datetime-local']:hover, 
[type='email']:hover, 
[type='month']:hover, 
[type='number']:hover, 
[type='password']:hover, 
[type='search']:hover, 
[type='tel']:hover, 
[type='text']:hover, 
[type='time']:hover, 
[type='url']:hover, 
[type='week']:hover, 
input:not([type]):hover, 
textarea:hover {
    background-color: orange;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try to style the **focus state** of the inputs. 
{{< hint info >}}
I'm not going to try all of them, but feel free to try with the other values as well!
{{< /hint >}}
{{< highlight scss >}}
@include gls-all-text-inputs(focus) {
    background-color: green;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
[type='color']:focus, [type='date']:focus, [type='datetime']:focus, [type='datetime-local']:focus, [type='email']:focus, [type='month']:focus, [type='number']:focus, [type='password']:focus, [type='search']:focus, [type='tel']:focus, [type='text']:focus, [type='time']:focus, [type='url']:focus, [type='week']:focus, input:not([type]):focus, textarea:focus {
    background-color: green;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Call the mixin in a selector to target only those text-based input elements inside that selector.
{{< highlight scss >}}
.containing-element {
    @include gls-all-text-inputs {
        background-color: green;
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.containing-element [type='color'], 
.containing-element [type='date'], 
.containing-element [type='datetime'], 
.containing-element [type='datetime-local'], 
.containing-element [type='email'], 
.containing-element [type='month'], 
.containing-element [type='number'], 
.containing-element [type='password'], 
.containing-element [type='search'], 
.containing-element [type='tel'], 
.containing-element [type='text'], 
.containing-element [type='time'], 
.containing-element [type='url'], 
.containing-element [type='week'], 
.containing-element input:not([type]), 
.containing-element textarea {
    background-color: green;
}
{{< /highlight >}}
{{< /highlightwrap >}}