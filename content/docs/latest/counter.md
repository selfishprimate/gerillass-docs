---
title: "Counter"
---

# Counter

{{< mixin type="Mixin" name="counter" >}}
**Counter** Sass mixin allows you to present your content in a **listicle** format. 
{{< hint info >}}
**Important:** The mixin must be applied to the parent element that has `counter-start` class on it, so all the children that have `counter-item` class will be affected.
{{< /hint >}}
{{< hint warning >}}
**Tip:** Somehow, **if you want to continue a list** that is interrupted by another content, simply give the containing element **'counter-continue'** class instead of **'counter-start'**.
{{< /hint >}}
The markup should look like the example below:
{{< highlight html >}}
<div class="listicle-wrapper counter-start">
    <div class="item counter-item">LISTICLE ITEM 01</div>
    <div class="item counter-item">LISTICLE ITEM 02</div>
    <div class="item counter-item">LISTICLE ITEM 03</div>
</div>
{{< /highlight >}}
{{< /mixin >}}

## Arguments

{{< arguments/table footnote="Pass `both` value to center an element on both the horizontal and vertical axes, or do not pass at all.">}}
    {{< arguments/row name="$counter" type="string" description="Sets the style of the counter. Default value is `decimal`. Check out the [links](#related-links) at the end of the article to learn more about the counter styles." >}}
    {{< arguments/row name="$counter-before" type="string" description="It helps you add a string before the counter." >}}
    {{< arguments/row name="$counter-after" type="string" description="It helps you add a string after the counter." >}}
{{< /arguments/table >}}


## Examples

Suppose you have a markup like in the below and you want to present it in a listicle format (the following markup will be used for all examples).

{{< highlight html >}}

<div class="listicle-wrapper counter-start">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>

{{< /highlight >}}

{{< highlightwrap class="example">}}
Simply call the mixin in a parent element's selector without passing any arguments.
{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter;
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: counter(glsCounter);
    counter-increment: glsCounter;
}
{{< /highlight >}}
<style>
.listicle-wrapper{
    background-color: whitesmoke;
    padding: 20px;
}
.listicle-wrapper .item:not(:last-child){
    margin-bottom: 1em;
}
.listicle-wrapper.example01.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.example01.counter-start .counter-item::before,
.listicle-wrapper.example01.counter-continue .counter-item::before {
    content: counter(glsCounter);
    counter-increment: glsCounter;
}
</style>
<div class="sandbox listicle-wrapper counter-start example01">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's highlight the counter a little more. **You can pass a decleration block into the mixin** to achieve that easily.
{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter {
        color: rgb(0, 85, 187);
        font-size: 1.1em;
        font-weight: bold;
        margin-right: 5px;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: counter(glsCounter);
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
{{< /highlight >}}
<style>
.listicle-wrapper.example02.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.example02.counter-start .counter-item::before,
.listicle-wrapper.example02.counter-continue .counter-item::before {
    content: counter(glsCounter);
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
</style>
<div class="sandbox listicle-wrapper counter-start example02">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's **change the counter style from `decimal` to `upper-roman`** (default is always `decimal`).
{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter(upper-roman) {
        color: rgb(0, 85, 187);
        font-size: 1.1em;
        font-weight: bold;
        margin-right: 5px;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: counter(glsCounter, upper-roman);
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
{{< /highlight >}}
<style>
.listicle-wrapper.example03.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.example03.counter-start .counter-item::before,
.listicle-wrapper.example03.counter-continue .counter-item::before {
    content: counter(glsCounter, upper-roman);
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
</style>
<div class="sandbox listicle-wrapper counter-start example03">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's try something different.
{{< hint info >}}
**Important:** Values ​​that you pass outside the predefined values ​​for **counter style** will be placed either **in front** or **behind** of the counter. If you pass **only one** value **it will be placed behind the counter**. If you pass **two values**, the **first one** will be placed **in front** of the counter and the **second** is **behind**.
{{< /hint >}}
{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter("____") {
        color: rgb(0, 85, 187);
        font-size: 1.1em;
        font-weight: bold;
        margin-right: 5px;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: counter(glsCounter) "____";
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
{{< /highlight >}}
<style>
.listicle-wrapper.example04.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.example04.counter-start .counter-item::before,
.listicle-wrapper.example04.counter-continue .counter-item::before {
    content: counter(glsCounter) "____";
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
</style>
<div class="sandbox listicle-wrapper counter-start example04">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's pass two values, one for the front of the counter the other one is for behind.
{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter("( ", " ) ") {
        color: rgb(0, 85, 187);
        font-size: 1.1em;
        font-weight: bold;
        margin-right: 5px;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: "( " counter(glsCounter) " ) ";
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
{{< /highlight >}}
<style>
.listicle-wrapper.example05.counter-start {
  counter-reset: glsCounter;
}
.listicle-wrapper.example05.counter-start .counter-item::before,
.listicle-wrapper.example05.counter-continue .counter-item::before {
  content: "( " counter(glsCounter) " ) ";
  counter-increment: glsCounter;
  color: rgb(0, 85, 187);
  font-size: 1.1em;
  font-weight: bold;
  margin-right: 5px;
}
</style>
<div class="sandbox listicle-wrapper counter-start example05">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's pass `decimal` value for the counter style and add a string behind it!
{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter(decimal, "th ") {
        color: rgb(0, 85, 187);
        font-size: 1.1em;
        font-weight: bold;
        margin-right: 5px;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: counter(glsCounter, decimal) "th ";
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
{{< /highlight >}}
<style>
.listicle-wrapper.example06.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.example06.counter-start .counter-item::before,
.listicle-wrapper.example06.counter-continue .counter-item::before {
    content: counter(glsCounter, decimal) "th ";
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
</style>
<div class="sandbox listicle-wrapper counter-start example06">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's **add a string in front of the counter** and pass `decimal-leading-zero` value for counter style.
{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter("Section ", decimal-leading-zero) {
        color: rgb(0, 85, 187);
        font-size: 1.1em;
        font-weight: bold;
        margin-right: 5px;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: "Section " counter(glsCounter, decimal-leading-zero);
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
{{< /highlight >}}
<style>
.listicle-wrapper.example07.counter-start {
  counter-reset: glsCounter;
}
.listicle-wrapper.example07.counter-start .counter-item::before,
.listicle-wrapper.example07.counter-continue .counter-item::before {
  content: "Section " counter(glsCounter, decimal-leading-zero);
  counter-increment: glsCounter;
  color: rgb(0, 85, 187);
  font-size: 1.1em;
  font-weight: bold;
  margin-right: 5px;
}
</style>
<div class="sandbox listicle-wrapper counter-start example07">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
Now let's add a string to both the front and behind of the counter.
{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter("[ Section ", decimal-leading-zero, " ]") {
        color: rgb(0, 85, 187);
        font-size: 1.1em;
        font-weight: bold;
        margin-right: 5px;
    };
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: "[ Section " counter(glsCounter, decimal-leading-zero) " ]";
    counter-increment: glsCounter;
    color: rgb(0, 85, 187);
    font-size: 1.1em;
    font-weight: bold;
    margin-right: 5px;
}
{{< /highlight >}}
<style>
.listicle-wrapper.example08.counter-start {
  counter-reset: glsCounter;
}
.listicle-wrapper.example08.counter-start .counter-item::before,
.listicle-wrapper.example08.counter-continue .counter-item::before {
  content: "[ Section " counter(glsCounter, decimal-leading-zero) " ]";
  counter-increment: glsCounter;
  color: rgb(0, 85, 187);
  font-size: 1.1em;
  font-weight: bold;
  margin-right: 5px;
}
</style>
<div class="sandbox listicle-wrapper counter-start example08">
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone.</div>
    <div class="item counter-item">The purpose of lorem ipsum is to create a natural looking block of text.</div>
    <div class="item counter-item">More difficult to find examples of lorem ipsum in use before Letraset made it popular.</div>
    <div class="item counter-item">McClintock says he remembers coming across the lorem ipsum passage in a book of old metal.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
The examples shown so far were about how to use this function. **So where can you go from here?** Here is an example!
{{< highlight html >}}
<div class="listicle-wrapper counter-start">
    <div class="item counter-item">The passage experienced a surge in popularity during the 1960s when Letraset used it on their dry-transfer sheets, and again during the 90s as desktop publishers bundled the text with their software. Today it's seen all around the web; on templates, websites, and stock designs. Use our generator to get your own, or read on for the authoritative history of lorem ipsum.</div>
    <div class="item counter-item">Until recently, the prevailing view assumed lorem ipsum was born as a nonsense text. “It's not Latin, though it looks like it, and it actually says nothing,” Before & After magazine answered a curious reader, “Its ‘words’ loosely approximate the frequency with which letters occur in English, which is why at a glance it looks pretty real.”</div>
    <div class="item counter-item">Richard McClintock, a Latin scholar from Hampden-Sydney College, is credited with discovering the source behind the ubiquitous filler text. In seeing a sample of lorem ipsum, his interest was piqued by consectetur—a genuine, albeit rare, Latin word. Consulting a Latin dictionary led McClintock to a passage from De Finibus Bonorum et Malorum (“On the Extremes of Good and Evil”), a first-century B.C. text from the Roman philosopher Cicero.</div>
    <div class="item counter-item">It's difficult to find examples of lorem ipsum in use before Letraset made it popular as a dummy text in the 1960s, although McClintock says he remembers coming across the lorem ipsum passage in a book of old metal type samples. So far he hasn't relocated where he once saw the passage, but the popularity of Cicero in the 15th century supports the theory that the filler text has been used for centuries.</div>
    <div class="item counter-item">As an alternative theory, (and because Latin scholars do this sort of thing) someone tracked down a 1914 Latin edition of De Finibus which challenges McClintock's 15th century claims and suggests that the dawn of lorem ipsum was as recent as the 20th century. The 1914 Loeb Classical Library Edition ran out of room on page 34 for the Latin phrase “dolorem ipsum” (sorrow in itself). Thus, the truncated phrase leaves one page dangling with “do-”, while another begins with the now ubiquitous “lorem ipsum”.</div>
</div>
{{< /highlight >}}

{{< highlight scss >}}
.listicle-wrapper {
    @include gls-counter {
        position: absolute;
        top: 0;
        left: 0;
        font-size: 7em;
        font-weight: bold;
        font-style: italic;
        font-family: "Jumble", sans-serif;
        transform: translateY(-20%);
        color: rgb(230,230,230);
        line-height: 1;
        z-index: -1;
    };
    .item {
        position: relative;
        padding-left: 50px;
        &:not(:last-child) {
            margin-bottom: 3rem;
        }
    }
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.listicle-wrapper.counter-start {
    counter-reset: glsCounter;
}
.listicle-wrapper.counter-start .counter-item::before,
.listicle-wrapper.counter-continue .counter-item::before {
    content: counter(glsCounter);
    counter-increment: glsCounter;
    position: absolute;
    top: 0;
    left: 0;
    font-size: 7em;
    font-weight: bold;
    font-style: italic;
    font-family: "Jumble", sans-serif;
    transform: translateY(-20%);
    color: #e6e6e6;
    line-height: 1;
    z-index: -1;
}
.listicle-wrapper .item {
    position: relative;
    padding-left: 50px;
}
.listicle-wrapper .item:not(:last-child) {
    margin-bottom: 3rem;
}
{{< /highlight >}}
<style>
.listicle-wrapper.example09.counter-start {
  counter-reset: glsCounter;
  background-color: transparent;
}
.listicle-wrapper.example09.counter-start .counter-item::before,
.listicle-wrapper.example09.counter-continue .counter-item::before {
  content: counter(glsCounter);
  counter-increment: glsCounter;
  position: absolute;
  top: 0;
  left: 0;
  font-size: 7em;
  font-style: italic;
  font-family: "Jumble", sans-serif;
  -webkit-transform: translateY(-20%);
  transform: translateY(-20%);
  color: #e6e6e6;
  line-height: 1;
  z-index: -1;
}
.listicle-wrapper.example09 .item {
  position: relative;
  padding-left: 50px;
}
.listicle-wrapper.example09 .item:not(:last-child) {
  margin-bottom: 3rem;
}
</style>
<div class="listicle-wrapper counter-start example09">
    <div class="item counter-item"><strong>The passage experienced a surge in popularity</strong> during the 1960s when Letraset used it on their dry-transfer sheets, and again during the 90s as desktop publishers bundled the text with their software. Today it's seen all around the web; on templates, websites, and stock designs. Use our generator to get your own, or read on for the authoritative history of lorem ipsum.</div>
    <div class="item counter-item"><strong>Until recently</strong>, the prevailing view assumed lorem ipsum was born as a nonsense text. “It's not Latin, though it looks like it, and it actually says nothing,” Before & After magazine answered a curious reader, “Its ‘words’ loosely approximate the frequency with which letters occur in English, which is why at a glance it looks pretty real.”</div>
    <div class="item counter-item"><strong>Richard McClintock</strong>, a Latin scholar from Hampden-Sydney College, is credited with discovering the source behind the ubiquitous filler text. In seeing a sample of lorem ipsum, his interest was piqued by consectetur—a genuine, albeit rare, Latin word. Consulting a Latin dictionary led McClintock to a passage from De Finibus Bonorum et Malorum (“On the Extremes of Good and Evil”), a first-century B.C. text from the <strong>Roman philosopher Cicero</strong>.</div>
    <div class="item counter-item"><strong>It's difficult to find examples of lorem ipsum in use before Letraset made it popular as a dummy text in the 1960s, although McClintock says he remembers coming across the lorem ipsum passage in a book of old metal type samples</strong>. So far he hasn't relocated where he once saw the passage, but the popularity of Cicero in the 15th century supports the theory that the filler text has been used for centuries.</div>
    <div class="item counter-item"><strong>As an alternative theory</strong>, (and because Latin scholars do this sort of thing) someone tracked down a 1914 Latin edition of De Finibus which challenges McClintock's 15th century claims and suggests that the dawn of lorem ipsum was as recent as the 20th century. The 1914 Loeb Classical Library Edition ran out of room on page 34 for the Latin phrase “dolorem ipsum” (sorrow in itself). Thus, the truncated phrase leaves one page dangling with “do-”, while another begins with the now ubiquitous “lorem ipsum”.</div>
</div>
{{< /highlightwrap >}}

{{< highlightwrap class="example">}}
If you want **to continue a list that is interrupted by another content**, simply give the continuing parent element **‘counter-continue’** class instead of **‘counter-start’**.
{{< highlight html >}}
<div class="listicle-wrapper counter-start">
    <div class="item counter-item">The passage experienced a surge in popularity during the 1960s when Letraset used it on their dry-transfer sheets, and again during the 90s as desktop publishers bundled the text with their software. Today it's seen all around the web; on templates, websites, and stock designs. Use our generator to get your own, or read on for the authoritative history of lorem ipsum.</div>
    <div class="item counter-item">Until recently, the prevailing view assumed lorem ipsum was born as a nonsense text. “It's not Latin, though it looks like it, and it actually says nothing,” Before & After magazine answered a curious reader, “Its ‘words’ loosely approximate the frequency with which letters occur in English, which is why at a glance it looks pretty real.”</div>
    <div class="item counter-item">Richard McClintock, a Latin scholar from Hampden-Sydney College, is credited with discovering the source behind the ubiquitous filler text. In seeing a sample of lorem ipsum, his interest was piqued by consectetur—a genuine, albeit rare, Latin word. Consulting a Latin dictionary led McClintock to a passage from De Finibus Bonorum et Malorum (“On the Extremes of Good and Evil”), a first-century B.C. text from the Roman philosopher Cicero.</div>
</div>
<div class="image-container" style="height: 300px; margin-bottom: 16px; background-image: url(https://i.picsum.photos/id/1015/6000/4000.jpg); background-size:cover; background-position: center;"></div>
<div class="listicle-wrapper counter-continue">
    <div class="item counter-item">The passage experienced a surge in popularity during the 1960s when Letraset used it on their dry-transfer sheets, and again during the 90s as desktop publishers bundled the text with their software. Today it's seen all around the web; on templates, websites, and stock designs. Use our generator to get your own, or read on for the authoritative history of lorem ipsum.</div>
    <div class="item counter-item">Until recently, the prevailing view assumed lorem ipsum was born as a nonsense text. “It's not Latin, though it looks like it, and it actually says nothing,” Before & After magazine answered a curious reader, “Its ‘words’ loosely approximate the frequency with which letters occur in English, which is why at a glance it looks pretty real.”</div>
    <div class="item counter-item">Richard McClintock, a Latin scholar from Hampden-Sydney College, is credited with discovering the source behind the ubiquitous filler text. In seeing a sample of lorem ipsum, his interest was piqued by consectetur—a genuine, albeit rare, Latin word. Consulting a Latin dictionary led McClintock to a passage from De Finibus Bonorum et Malorum (“On the Extremes of Good and Evil”), a first-century B.C. text from the Roman philosopher Cicero.</div>
</div>
{{< /highlight >}}

<style>
.listicle-wrapper.example10.counter-start {
  counter-reset: glsCounter;
  background-color: transparent;
}
.listicle-wrapper.counter-continue {
  background-color: transparent;
}
.listicle-wrapper.example10.counter-start .counter-item::before,
.listicle-wrapper.example10.counter-continue .counter-item::before {
  content: counter(glsCounter);
  counter-increment: glsCounter;
  position: absolute;
  top: 0;
  left: 0;
  font-size: 7em;
  font-style: italic;
  font-family: "Jumble", sans-serif;
  -webkit-transform: translateY(-20%);
  transform: translateY(-20%);
  color: #e6e6e6;
  line-height: 1;
  z-index: -1;
}
.listicle-wrapper.example10 .item {
  position: relative;
  padding-left: 50px;
}
.listicle-wrapper.example10 .item:not(:last-child) {
  margin-bottom: 3rem;
}
</style>
<div class="listicle-wrapper counter-start example10">
    <div class="item counter-item"><strong>The passage experienced a surge in popularity</strong> during the 1960s when Letraset used it on their dry-transfer sheets, and again during the 90s as desktop publishers bundled the text with their software. Today it's seen all around the web; on templates, websites, and stock designs. Use our generator to get your own, or read on for the authoritative history of lorem ipsum.</div>
    <div class="item counter-item"><strong>Until recently</strong>, the prevailing view assumed lorem ipsum was born as a nonsense text. “It's not Latin, though it looks like it, and it actually says nothing,” Before & After magazine answered a curious reader, “Its ‘words’ loosely approximate the frequency with which letters occur in English, which is why at a glance it looks pretty real.”</div>
    <div class="item counter-item"><strong>Richard McClintock</strong>, a Latin scholar from Hampden-Sydney College, is credited with discovering the source behind the ubiquitous filler text. In seeing a sample of lorem ipsum, his interest was piqued by consectetur—a genuine, albeit rare, Latin word. Consulting a Latin dictionary led McClintock to a passage from De Finibus Bonorum et Malorum (“On the Extremes of Good and Evil”), a first-century B.C. text from the <strong>Roman philosopher Cicero</strong>.</div>
</div>
<div class="image-container" style="border-radius: 3px;height: 300px; margin-bottom: 16px;background-image: url(https://i.picsum.photos/id/1015/6000/4000.jpg); background-size: cover; background-position: center;"></div>
<div class="listicle-wrapper counter-continue example10">
    <div class="item counter-item"><strong>Richard McClintock</strong>, a Latin scholar from Hampden-Sydney College, is credited with discovering the source behind the ubiquitous filler text. In seeing a sample of lorem ipsum, his interest was piqued by consectetur—a genuine, albeit rare, Latin word. Consulting a Latin dictionary led McClintock to a passage from De Finibus Bonorum et Malorum (“On the Extremes of Good and Evil”), a first-century B.C. text from the <strong>Roman philosopher Cicero</strong>.</div>
    <div class="item counter-item"><strong>It's difficult to find examples of lorem ipsum in use before Letraset made it popular as a dummy text in the 1960s, although McClintock says he remembers coming across the lorem ipsum passage in a book of old metal type samples</strong>. So far he hasn't relocated where he once saw the passage, but the popularity of Cicero in the 15th century supports the theory that the filler text has been used for centuries.</div>
    <div class="item counter-item"><strong>As an alternative theory</strong>, (and because Latin scholars do this sort of thing) someone tracked down a 1914 Latin edition of De Finibus which challenges McClintock's 15th century claims and suggests that the dawn of lorem ipsum was as recent as the 20th century. The 1914 Loeb Classical Library Edition ran out of room on page 34 for the Latin phrase “dolorem ipsum” (sorrow in itself). Thus, the truncated phrase leaves one page dangling with “do-”, while another begins with the now ubiquitous “lorem ipsum”.</div>
</div>
{{< /highlightwrap >}}

## Related Links

* [7 Tips for Writing a Great Listicle](https://compose.ly/for-writers/7-tips-for-writing-a-great-listicle/)
* [CSS Pseudo Element Counters...](https://stackoverflow.com/questions/16943805/css-pseudo-element-counters-can-you-increment-an-alphabet-letter-a-b-c)
* [Numbering in Style](https://css-tricks.com/numbering-in-style/)