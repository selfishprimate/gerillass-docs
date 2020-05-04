---
title: "Reset CSS"
---

# Reset CSS

{{< featured type="Mixin" name="reset-css" >}}
**Reset CSS** mixin (also known as **CSS Reset**) helps you to reset the browser default styles of all HTML elements to a consistent baseline.
{{< hint info >}}
Endless thanks to [**Eric Meyer**](https://meyerweb.com/) for his legendary [**Reset CSS**](https://meyerweb.com/eric/tools/css/reset/) code that used for years and allowing us to include it to this library.
{{< /hint >}}
{{< /featured >}}

## Examples

{{< highlightwrap class="example">}}
Simply call the mixin at the root of your style sheet to override browser default styles.
{{< highlight scss >}}
@include gls-reset-css;
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, main, nav, section {
    display: block;
}
body {
    line-height: 1;
}
ol, ul {
    list-style: none;
}
blockquote, q {
    quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
    content: '';
    content: none;
}
table {
    border-collapse: collapse;
    border-spacing: 0;
}
{{< /highlight >}}
{{< /highlightwrap >}}

## Related Articles
* [CSS Tools: Reset CSS](https://meyerweb.com/eric/tools/css/reset/)
* [What is a CSS Reset?](https://cssreset.com/what-is-a-css-reset/)
* [Browsers' default CSS for HTML elements](https://stackoverflow.com/questions/6867254/browsers-default-css-for-html-elements)
