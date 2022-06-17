# Detect User

This is a conditional event that should only be fired in very specific cases. It is intended to cover cases where a user authentication system exists on the site but the user authentication state may not be known by the time the page_view event is sent. In that case, send this event as soon as the user authentication state is known.

The configuration tag should be refired on this event to capture the user_id.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null, userModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "detect_user",
  userModel: {
    authentication_method: "<authentication_method>",
    user_id: "<user_id>",
    user_login_state: '<user_login_state>',
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|authentication_method|string|recommended|The method by which a user authenticated. Only send if available.|username-and-password,google,github|
|user_id|string|recommended|The user identifier|1234567890|
|user_login_state|string|contextual|The user authentication state|authenticated, anonymous|