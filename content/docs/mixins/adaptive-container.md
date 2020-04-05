# Adaptive Container

{{< github link="adaptive-container" >}}

{{< subheader value="Mixin" mixin-call="adaptive-container" >}}

The passage experienced a surge in popularity during the 1960s when Letraset used it on their dry-transfer sheets, and again during the 90s as desktop publishers bundled the text with their software.

During the 1960s when Letraset used it on their dry-transfer sheets, and again during the 90s as desktop publishers bundled the text with their software.

{{< /subheader >}}

## Arguments

{{< arguments/table footnote="Sentiet et ferali errorem fessam, coercet superbus, Ascaniumque in pennis mediis dolor!" >}}

    {{< arguments/row name="$values" type="list" description="List of border styles; accepts CSS shorthand." >}}

    {{< arguments/row name="$dark" type="string" description="Dark `colored` border styles; accepts CSS shorthand." >}}

{{< /arguments/table >}}

## Examples

Sentiet et ferali errorem fessam, coercet superbus, Ascaniumque in pennis
mediis; dolor?

{{< highlight scss >}}
.element {
  @include gls-adaptive-container(30px);
}

// CSS Output
.inner-container{
    display: flex;
    justify-content: center;
    align-items: center;
}

{{< /highlight >}}






