# View Item (Product) List

Fire whenever a user sees multiple product links in a list that forward the user to the product detail page. 

This event should also be fired for the "Filter By Group" component when the list is initially displayed or updated after a facet is applied...but only when that component contains products.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_item_list",
  ecommerce: {
    facets: "<facets>",
    items: "<items>",
    item_list_id: "<item_list_id>",
    item_list_name: "<item_list_name>",
    list_type: "<list_type>",
    search_term: "<search_term>",
    search_type: "<search_type>",
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|facets|delimited string|contextual|A double-delimited string of key/value pairs representing the refinements that were applied to this search. Only set if the list type is a search result or filter_by_group.|category:generic products~color:blue~featured_as:best_seller|
|items|array of [items](/schemas/item.md)|required|Populate with only the item that was selected. This should always be a single item array.|`[{item_id: "sandwich1", item_name="CFA Chicken Sandwich"}]`
|item_list_id|string|recommended|The computer-readable machine name of the list the item showed up in. Use UUID provided by the component if no more specific ID is available.|12345abcde12345|
|item_list_name|string|recommended|The human-readable name of the list the item showed up in. If one is not available, populate with numerical index of which list this is on the page (1-indexed).|recommended_products, recently_viewed_products|
|list_type|string|contextual|The type of list the item was found in.|cards, search_results|
|search_term|string|contextual|The final search term submitted after any correction has been performed. Only set if the `list_type` is `search_results`.|blue widgets|
|search_type|string|contextual|The type of search performed. Only set if the `list_type` is `search_results`.|site,product,article|
