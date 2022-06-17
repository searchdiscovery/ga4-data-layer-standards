# Click

These events will be automatically detected and fired for any `<a>` tag clicked by a user. The data attributes and events are primarily here for cases in which a non anchor tag is used as a link. 

For example, if a `<button>` tag is used in combination with Javascript to represent a download link, you would need to add these attributes to fire the event.

## HTML Data Attributes

```html
<button
  data-layer-event="click"
  data-layer-category="<category>"
  data-layer-category2="<category2>"
  data-layer-category3="<category3>"
  data-layer-category4="<category4>"
  data-layer-category5="<category5>"
  data-layer-identifier="<identifier>"
  data-layer-link_text="<link_text>"
  data-layer-link_url="<link_url>"
  data-layer-outbound="<outbound>"
  data-layer-protocol="<protocol>"
>
```

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "click",
  eventModel: {
    category: "<category>",
    category2: "<category2>",
    category3: "<category3>",
    category4: "<category4>",
    category5: "<category5>",
    component_ancestry: "<component_ancestry>",
    identifier: "<identifier>",
    link_classes: "<link_classes>",
    link_id: "<link_id>",
    link_text: "<link_text>",
    link_url: "<link_url>",
    navigation_ancestry: "<navigation_ancestry>",
    outbound: "<outbound>",
    region_ancestry: "<region_ancestry>",
    protocol: "<protocol>",
  }
});
```

## Variable Definitions

|Field|Type|Required?|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|component_ancestry|string|recommended|A delimited string showing all components in the ancestry of the link clicked|hero~product carousel
|category|string|optional|Optional field that enables you to assign this link a specific category. Used primarily when you want to analyze the performance of a group of links that aren't connected by component_ancestry, region_ancestry, link_url, or link_text.|cta_links, wtb_links|
|category[2-5]|string|optional|Optional fields that enable you to assign this link additional subcategories beyond category.|cta_links, wtb_links|
|identifier|string|optional|Optional field that enables you to assign this link a specific ID. Used primarily when you need to identify a link and component_ancestry, region_ancestry, link_classes, link_id, link_text, and link_url are not sufficient to do that. Useful if there is a specific link on a site that may change URL/text in the future but still needs to represent the same link/CTA concept.|app_download|
|link_classes|string|required|The list of HTML/CSS classes applied to the link.|button-red|
|link_domain|string|required|The domain of the link.|example.com|
|link_id|string|required|The HTML/CSS ID of the link.|submit-button|
|link_text|string|required|The full text of the link.|click here|
|link_url|string|required|The full URL of the link.|https://www.widgets.com/form|
|navigation_ancestry|string|recommended|A delimited string showing all navigation items in the ancestry of link clicked in a multi-tiered menu|about~our leadership~our CEO|
|outbound|boolean|conditional|Does the link point to a different domain?|false|
|region_ancestry|string|recommended|A delimited string showing all regions in the ancestry of the link clicked|header~navigation|
|protocol|string|required|Records the protocol of link that was clicked. The protocol here refers to what comes before the :// on the link itself. Useful for identifying http links that should be https, as well as reporting on mailto, tel, and other alternate link types|http, https, tel, mailto|
