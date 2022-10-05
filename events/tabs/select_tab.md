# Select Tab

Fire whenever a user selects a an item out of a tabset that asynchronously updates the page. Do not use this for navigation menus as those should be covered by [menu data attributes](/data-attributes/menus.md).

<img width="611" alt="image" src="https://user-images.githubusercontent.com/60939634/179827280-c654c364-8351-45fd-80f8-2ce3fc41af31.png">


## HTML Data Attributes

```html
<a href="<link_url>"
  data-layer-event="select_tab"
  data-layer-identifier="<identifier>"
  data-layer-name="<name>"
  data-layer-heading="<heading>"
  data-layer-index="<index>"
>
```
## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "select_tab",
  eventModel: {
    identifier: "<identifier>",
    name: "<name>",
    heading: "<heading>",
    index: "<index>",
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|identifier|string|required|The computer-readable machine name of the tab. Use UUID provided by the component|12345abcde12345|
|name|string|recommended|The human-readable name of the tab. If user does not input one, populate with numerical index of which tab this is on the page (1-indexed). FAQs are the big one that currently need to be broken out in reporting, so getting a name for those should be the priority.|FAQs, 2|
|heading|string|required|The text heading of the tab item that was opened/closed|"What's a widget? Does anyone really know?"|
|index|integer|recommended|The ordinal slot number of the tab item. E.g. - the top item in the tab will be slot 1. (1-indexed)|1||1||1|
