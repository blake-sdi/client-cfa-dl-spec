# View Search Results

Fire whenever a user views search results. This includes product searches, content searches, resource searches, etc. and does not require a search event to be fired prior to it.

This event should also be considered for the "Filter By Group" component if it is ever used to display anything but products. When used in this way, the search_term parameter would be `filter_by_group` as that component does not currently allow for a search_term to be entered by the user. If this case does arise, contact Search Discovery for additional information.
## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "view_search_results",
  eventModel: {
    facets: "<refinements>",
    number_of_items: "<number_of_items>",
    search_term: "<search_term>",
    search_type: "<search_type>",
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|facets|delimited string|recommended|A delimited string of key/value pairs representing the facets that were applied to this search|need:skin health\~skin_concern:acne\~featured_as:best_seller|
|number_of_items|integer|recommended|The total number of search results found|324|
|search_term|string|required|The final search term submitted after any correction has been performed|blue widgets|
|search_term_corrected|string|recommended|The initial search term before typeahead/lookahead/suggestion, if the site has those features.|blue w|
|search_type|string|required|The type of search performed|site,product,article|
