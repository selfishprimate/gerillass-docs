---
title: "All Text Inputs"
---

# All Text Inputs

{{< featured type="Mixin" name="all-text-inputs" >}}
**All Text Inputs** Sass mixin helps you to target all the text-based HTML input elements in the DOM, thus you can easily apply your style rules.
{{< /featured >}}

## Arguments

{{< arguments/table footnote="You can call the mixin either at the root level of your style sheet to target all the text-based input elements in the DOM or call it in a selector to target only some particular elements as children of the given selector.">}}
    {{< arguments/row name="$pseudo" type="string" description="Sets the pleudo-class selector of the selected text-based input elements. Accepts `hover`, `focus`, `active`, `invalid`, `required`, `disabled` values." >}}
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
Let's target all the text-based HTML inputs with the **:hover** pseudo-class selector applied. 
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
Let's target all the text-based HTML inputs with the **:focus** pseudo-class selector applied. 
{{< highlight scss >}}
@include gls-all-text-inputs(focus) {
    background-color: green;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
[type='color']:focus, 
[type='date']:focus, 
[type='datetime']:focus, 
[type='datetime-local']:focus, 
[type='email']:focus, 
[type='month']:focus, 
[type='number']:focus, 
[type='password']:focus, 
[type='search']:focus, 
[type='tel']:focus, 
[type='text']:focus, 
[type='time']:focus, 
[type='url']:focus, 
[type='week']:focus, 
input:not([type]):focus, 
textarea:focus {
    background-color: green;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's target all the text-based HTML inputs with the **:active** pseudo-class selector applied. 
{{< highlight scss >}}
.element {
    @include gls-all-text-inputs(active) {
        background-color: green;
        color: white;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element [type='color']:active, 
.element [type='date']:active, 
.element [type='datetime']:active, 
.element [type='datetime-local']:active, 
.element [type='email']:active, 
.element [type='month']:active, 
.element [type='number']:active, 
.element [type='password']:active, 
.element [type='search']:active, 
.element [type='tel']:active, 
.element [type='text']:active, 
.element [type='time']:active, 
.element [type='url']:active, 
.element [type='week']:active, 
.element input:not([type]):active, 
.element textarea:active {
    background-color: green;
    color: white;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's target all the text-based HTML inputs with the **:invalid** pseudo-class selector applied. 
{{< highlight scss >}}
.element {
    @include gls-all-text-inputs(invalid) {
        background-color: red;
        color: white;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element [type='color']:invalid, 
.element [type='date']:invalid, 
.element [type='datetime']:invalid, 
.element [type='datetime-local']:invalid, 
.element [type='email']:invalid, 
.element [type='month']:invalid, 
.element [type='number']:invalid, 
.element [type='password']:invalid, 
.element [type='search']:invalid, 
.element [type='tel']:invalid, 
.element [type='text']:invalid, 
.element [type='time']:invalid, 
.element [type='url']:invalid, 
.element [type='week']:invalid, 
.element input:not([type]):invalid, 
.element textarea:invalid {
    background-color: red;
    color: white;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try it with the **:required** pseudo-class selector applied. 
{{< highlight scss >}}
.element {
    @include gls-all-text-inputs(required) {
        background-color: orange;
        color: white;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element [type='color']:required, 
.element [type='date']:required, 
.element [type='datetime']:required, 
.element [type='datetime-local']:required, 
.element [type='email']:required, 
.element [type='month']:required, 
.element [type='number']:required, 
.element [type='password']:required, 
.element [type='search']:required, 
.element [type='tel']:required, 
.element [type='text']:required, 
.element [type='time']:required, 
.element [type='url']:required, 
.element [type='week']:required, 
.element input:not([type]):required, 
.element textarea:required {
    background-color: orange;
    color: white;
}
{{< /highlight >}}
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try it with **:disabled** pseudo-class selector applied. 
{{< highlight scss >}}
.element {
    @include gls-all-text-inputs(disabled) {
        background-color: gray;
        color: black;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.element [type='color']:disabled, 
.element [type='date']:disabled, 
.element [type='datetime']:disabled, 
.element [type='datetime-local']:disabled, 
.element [type='email']:disabled, 
.element [type='month']:disabled, 
.element [type='number']:disabled, 
.element [type='password']:disabled, 
.element [type='search']:disabled, 
.element [type='tel']:disabled, 
.element [type='text']:disabled, 
.element [type='time']:disabled, 
.element [type='url']:disabled, 
.element [type='week']:disabled, 
.element input:not([type]):disabled, 
.element textarea:disabled {
    background-color: gray;
    color: white;
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