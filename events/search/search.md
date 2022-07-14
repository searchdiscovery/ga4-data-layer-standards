# Search

Fire whenever a user performs a search of any kind. This includes product searches, content searches, resource searches, etc. and does not require a view_search_results event to be fired subsequent to it.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "search",
  eventModel: {
    corrected_term: "<search_term_corrected>",
    search_term: "<search_term>",
    search_type: "<search_type>",
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|search_term|string|required|The final search term submitted after any correction has been performed|eat more chicken|
|search_term_corrected|string|recommended|The initial search term before typeahead/lookahead/suggestion, if the site has those features.|eat mor chikin|
|search_type|string|required|The type of search performed|site,product,article|
