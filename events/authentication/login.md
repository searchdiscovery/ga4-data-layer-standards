# Login

Fire whenever a user logs in to an account.

The configuration tag should be refired on this event to capture the user_id.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ userModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "login",
  userModel: {
    authentication_method: "<method>",
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
|user_login_state|string|contextual|Set on all events with the authentication status of the visitor.|authenticated, anonymous|
