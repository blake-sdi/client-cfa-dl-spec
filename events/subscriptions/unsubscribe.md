# Unsubscribe

Fire whenever a user unsubscribes from an email or product.

## HTML Data Attributes

TBD

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ eventModel: null });  // Clear the previous eventModel object.
dataLayer.push({
  event: 'subscribe',
  eventModel: {
    identifier: '<identifier>',
    name: '<name>',
    type: '<type>',
    method: '<method>'
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|identifier|string|recommended|The subscription machine-readable name. This should be a unique value specific to this subscription, if one exists. If one does not exist, this can also be populated with the same value as the `name`.|widgets_newsletter_123, widget_promos_123|
|method|string|recommended|The channel through which the subscription was delivered. This is usually email, but can also be product.|email|
|name|string|required|The subscription human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the subscription with. It should be lowercase snake_case.|widgets_newsletter, widget_promos|
|type|string|required|The subscription type. This will act as a filtering mechanism in reporting to enable analysts to view subscription droppoff funnels. It can also act as an internal aid in firing additional events if necessary. For instance, lead-generating subscriptions require a `generate_lead` event to be fired alongside `form_complete`, and that could be written into the logic based upon this field.|newsletter, promos|