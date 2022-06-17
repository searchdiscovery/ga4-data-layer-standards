# Logout

Fire whenever a user logs out of an account.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ userModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: "logout",
  userModel: {
    user_id: "<user_id>",
    user_login_state: '<user_login_state>',
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|user_id|string|recommended|The user identifier|1234567890|
|user_login_state|string|contextual|Set on all events with the authentication status of the visitor.|anonymous|
