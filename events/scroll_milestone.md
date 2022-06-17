# Scroll Milestone

Fire when a user scrolls past a certain scroll depth. The built-in `scroll` event can be set up to automatically on 90% scroll depth, but this event will allow for more milestones to be recorded.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: 'scroll_milestone',
  eventModel: {
    milestone: '<milestone>'
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|milestone|string|required|The depth to which user scrolled on the page.|25,50,75|
