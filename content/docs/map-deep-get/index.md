---
title: "mapDeepGet"
page_title: "mapDeepGet Sass Function"
page_description: "Reads a value out of a nested map by following a chain of keys."
page_keywords: "Gerillass mapDeepGet, Sass mapDeepGet, Sass Functions, SCSS Functions, Sass Utility Functions, Gerillass Utilities"
---

# mapDeepGet

{{< function type="Function" name="mapDeepGet" file="map-deep-get" >}}
Reads a value out of a nested map by following a chain of keys.
{{< /function >}}

## Arguments

{{< arguments/table >}}
  {{< arguments/row name="$map" type="map" description="Accepts a map." >}}
  {{< arguments/row name="$keys…" type="string" description="Accepts one key per level of nesting." >}}
{{< /arguments/table >}}

## Examples

{{< highlightwrap class="example">}}
Reading two values out of one of the library's own maps.
{{< highlight scss >}}
.tablet-frame {
  width: mapDeepGet($map-for-tablets, "iPadPro", "width");
  height: mapDeepGet($map-for-tablets, "iPadPro", "height");
}
{{< /highlight >}}
{{< highlight css >}}
//CSS Output
.tablet-frame {
  width: 1024px;
  height: 1366px;
}
{{< /highlight >}}
{{< /highlightwrap >}}
