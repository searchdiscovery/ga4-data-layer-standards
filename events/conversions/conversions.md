# Conversions

Conversion events are just that...events whose only purpose is to act as a conversion in GA4 when the normal event is not specific enough to upgrade to a conversion.

For instance, perhaps on a site not every `form_complete` event should be a conversion. Lead forms should, but not contact us or report bug forms. As such, upgrading `form_complete` to a conversion is not a specific-enough event for ads to be optimized around. We would instead need another event to upgrade to a conversion...and whose only real purpose is to act as said conversion. Hence, conversion events.

Conversion events can be explictly fired through the data layer, automatically fired through click events, created dynamically through the tag manager based on another event, or created dynamically via the GA4 "Create Event" interface.

## HTML Data Attributes

```html
<div
  data-layer-event="conversion_eretailer_exit"
>

<div
  data-layer-event="conversion_video_start"
>

<div
  data-layer-event="conversion_app_download"
>
```

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "conversion_eretailer_exit",
});
dataLayer.push({
  event: "conversion_video_start",
});
dataLayer.push({
  event: "conversion_app_download",
});
```