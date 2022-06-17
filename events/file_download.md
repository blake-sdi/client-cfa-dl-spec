# File Download

These events will be automatically detected and fired for any link clicked by the user that leads to a file. The data attributes and events are primarily here for cases in which a non anchor tag is used as a link. 

For example, if a `<button>` tag is used in combination with Javascript to represent a download link, you would need to add these attributes to manually fire the event.

## HTML Data Attributes

```html
<a href="<link_url>"
  data-layer-event="file_download"
  data-layer-category="<category>"
  data-layer-category2="<category2>"
  data-layer-category3="<category3>"
  data-layer-category4="<category4>"
  data-layer-category5="<category5>"
  data-layer-component_ancestry="<component_ancestry>"
  data-layer-file_extension="<file_extension>"
  data-layer-file_name="<file_name>"
  data-layer-identifier="<identifier>"
  data-layer-link_url="<link_url>"
  data-layer-link_id="<link_id>"
  data-layer-link_classes="<link_classes>"
  data-layer-link_text="<link_text>"
  data-layer-navigation_ancestry="<navigation_ancestry>"
  data-layer-outbound="<outbound>"
  data-layer-region_ancestry="<region_ancestry>"
  data-layer-protocol="<protocol>"
>
```

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "file_download",
  eventModel: {
    category: "<category>",
    category2: "<category2>",
    category3: "<category3>",
    category4: "<category4>",
    category5: "<category5>",
    component_ancestry: "<component_ancestry>",
    file_extension: "<file_extension>",
    file_name: "<file_name>",
    identifier: "<identifier>",
    link_url: "<link_url>",
    link_id: "<link_id>",
    link_classes: "<link_classes>",
    link_text: "<link_text>",
    navigation_ancestry: "<navigation_ancestry>",
    outbound: "<outbound>",
    region_ancestry: "<region_ancestry>",
    protocol: "<protocol>"
  }
});
```

## Variable Definitions

|Field|Type|Required?|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|component_ancestry|string|recommended|A delimited string showing all components in the ancestry of the link clicked|hero~product carousel|
|file_extension|string|recommended|The file extension of the file being downloaded.|pdf|
|file_name|string|recommended|The filename of the file being downloaded.|drug_facts.pdf|
|identifier|string|optional|Optional field that enables you to assign this link a specific ID. Used primarily when you need to identify a link and component_ancestry, region_ancestry, link_classes, link_id, link_text, and link_url are not sufficient to do that.||
|link_classes|string|required|The list of HTML/CSS classes applied to the link.|button-red|
|link_domain|string|required|The domain of the link.|example.com|
|link_id|string|required|The HTML/CSS ID of the link.|submit-button|
|link_url|string|required|The full URL of the link.|https://www.example.com/form|
|navigation_ancestry|string|recommended|A delimited string showing all navigation items in the ancestry of link clicked in a multi-tiered menu|about~our leadership~our CEO|
|outbound|boolean|conditional|Does the link point to a different domain?|false|
|region_ancestry|string|recommended|A delimited string showing all regions in the ancestry of the link clicked|header~navigation
|protocol|string|required|Records the protocol of link that was clicked. The protocol here refers to what comes before the :// on the link itself. Useful for identifying http links that should be https, as well as reporting on mailto, tel, and other alternate link types|http, https, tel, mailto|
