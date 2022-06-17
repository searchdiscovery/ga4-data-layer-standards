# Sign Up

Fire whenever a user successfully creates an account.

The configuration tag should be refired on this event to capture the user_id.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: 'sign_up',
  userModel: {
    authentication_method: '<method>'
    user_id: "<user_id>",
    user_login_state: '<user_login_state>',
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|authentication_method|string|recommended|The authentication method with which a user created a new account.|local, social_login|

