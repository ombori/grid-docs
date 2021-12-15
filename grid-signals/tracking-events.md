# Event Tracking
Standard Session Events are pre-defined methods that are common accross different types of apps within the Grid. It is created so that the same events will have the same payload so we can easily build reports from the collected analytics data.

Standard Session Events are predefined events that are common across different types of apps within the Grid. It is created so that the same events will have the same payload so we can easily build reports from the collected analytics data.
- [Generic Events](/grid-signals/tracking-events?id=generic-events)
- [E-commerce Events](/grid-signals/tracking-events?id=e-commerce-events)
- [Contact Events](/grid-signals/tracking-events?id=contact-events)
- [Custom Events](/grid-signals/tracking-events?id=custom-event)

To use a method, take a look at this sample.

```javascript
import { eventTracking } from '@ombori/grid-session-manager';

eventTracking.sendRating({
    rating: 5,
    comment: "Amazing event tracking",
    interactionDelay: 988
});
```

All methods below are available on the `eventTracking` object, just like the `sendRating` method above. But just make sure you only send events *after* Grid Signals is initialized.

All events return a promise that resolves when the event is sent to the server, or the local cache in case the server is not available. There is no need to monitor the promise, as there also is no fail state. You can always assume the event is sent, either to cache or the server.

## Generic Events

- [sendContentView](/grid-signals/standard-session-events?id=sendcontentview)
- [sendRating](/grid-signals/standard-session-events?id=sendrating)
- [sendSearch](/grid-signals/standard-session-events?id=sendsearch)
- [sendSearchClear](/grid-signals/standard-session-events?id=sendsearchclear)

### sendContentView
```javascript
eventTracking.sendContentView(params);
```
Viewing a generic piece of content, equivalent to a "pageview" in old school web analytics
#### Parameters

| Name             | Type   | Required |
| ---------------- | ------ | -------- |
| `localizedTitle` | string | no       |
| `title`          | string | yes      |
| `url`            | string | no       |
### sendRating
```javascript
eventTracking.sendRating(params);
```

The user's rating of the experience

#### Parameters

| Name               | Type                  | Required |
| ------------------ | --------------------- | -------- |
| `comment`          | string                | yes      |
| `interactionDelay` | number                | yes      |
| `rating`           | 1 \| 2 \| 3 \| 4 \| 5 | yes      |
### sendSearch
```javascript
eventTracking.sendSearch(params);
```

Searching a product, category, or anything in the app

#### Parameters

| Name                | Type   |
| ------------------- | ------ |
| `searchQueryString` | string |
### sendSearchClear
```javascript
eventTracking.sendSearchClear();
```
Searching a product, category, or anything in the app
## E-commerce Events
- [sendCartView](/grid-signals/standard-session-events?id=e-commerce-events)
- [sendCartAdd](/grid-signals/standard-session-events?id=sendcartadd)
- [sendCartRemove](/grid-signals/standard-session-events?id=sendcartremove)
- [sendCartClear](/grid-signals/standard-session-events?id=sendcartclear)
- [sendCategoryView](/grid-signals/standard-session-events?id=sendcategoryview)
- [sendCheckout](/grid-signals/standard-session-events?id=sendcheckout)
- [sendLookView](/grid-signals/standard-session-events?id=sendlookview)
- [sendProductView](/grid-signals/standard-session-events?id=sendproductview)
- [sendPurchase](/grid-signals/standard-session-events?id=sendpurchase)

### sendCartView
```javascript
eventTracking.sendCartView();
```

Viewing the cart page
### sendCartAdd
```javascript
eventTracking.sendCartAdd(params);
```

Adding a product to the cart

#### Parameters

| Key         | Type   | Description                          | Required |
| ----------- | ------ | ------------------------------------ | -------- |
| `productId` | string | Product primary id used in PIM       | yes      |
| `quantity`  | number | Product quantity added into the cart | yes      |
### sendCartClear
```javascript
eventTracking.sendCartClear();
```

Clearing the cart
### sendCartRemove
```javascript
eventTracking.sendCartRemove(params);
```

Removing a product from the cart

#### Parameters

| Key         | Type   | Description                            | Required |
| ----------- | ------ | -------------------------------------- | -------- |
| `productId` | string | Product primary id used in PIM         | yes      |
| `quantity`  | number | Product quantity removed from the cart | yes      |
### sendCategoryView
```javascript
eventTracking.sendCategoryView(params);
```

Browsing products under a category

#### Parameters

| Key          | Type   | Description                     | Required |
| ------------ | ------ | ------------------------------- | -------- |
| `categoryId` | string | Category primary id used in PIM | yes      |
### sendCheckout
```javascript
eventTracking.sendCheckout();
```

Checkout step before payment
### sendLookView
```javascript
eventTracking.sendLookView(params);
```

Viewing a specific fashion look, which is an array of products

#### Parameters

| Key      | Type   | Required |
| -------- | ------ | -------- |
| `lookId` | string | yes      |
### sendProductView
```javascript
eventTracking.sendProductView(params);
```

Viewing a specific product page

#### Parameters

| Key         | Type   | Description                    | Required |
| ----------- | ------ | ------------------------------ | -------- |
| `productId` | string | Product primary id used in PIM | yes      |
### sendPurchase
```javascript
eventTracking.sendPurchase(params);
```

Payment success

#### Parameters

| Key             | Type   | Required |
| --------------- | ------ | -------- |
| `coupon`        | string | no       |
| `currencyCode`  | string | yes      |
| `revenue`       | number | yes      |
| `shipping`      | number | yes      |
| `tax`           | number | yes      |
| `transactionId` | string | yes      |
## Contact Events

- [sendContactIdentify](/grid-signals/standard-session-events?id=sendcontactidentify)
- [sendContactMetadata](/grid-signals/standard-session-events?id=sendcontactmetadata)
- [sendDetectAge](/grid-signals/standard-session-events?id=senddetectage)
- [sendDetectGender](/grid-signals/standard-session-events?id=senddetectgender)
- [sendDetectMood](/grid-signals/standard-session-events?id=senddetectmood)

### sendContactIdentify
```javascript
eventTracking.sendContactIdentify(params);
```

Identifying the customer based on a known identifier

#### Parameters

| Key           | Type    | Required | Description                                        |
| ------------- | ------- | -------- | -------------------------------------------------- |
| `contactType` | STRING  | yes      | Provide any of `PHONE`, `EMAIL` and `CLIENT_ID`    |
| `contact`     | string  | yes      | Enter the value of `contactType`                   |
| `interaction` | boolean | yes      | Whether the event was triggered by the user or not |
### sendContactMetadata
```javascript
eventTracking.sendContactMetadata(params);
```

Identifying the customer based on a known identifier.

#### Parameters

| Key           | Type    | Required | Description                                        |
| ------------- | ------- | -------- | -------------------------------------------------- |
| `interaction` | boolean | yes      | Whether the event was triggered by the user or not |
| `str1`        | string  | yes      | Provide any of `PHONE`, `EMAIL` and `CLIENT_ID`    |
| `str2`        | string  | yes      | The value of the `str1` field                      |
### sendDetectAge
```javascript
eventTracking.sendDetectAge(params);
```
Information about the user, returned from computer vision, 3rd party services, or selected by a user in the UI
Note, this method will update the Contact Metadata but it will also log the values for analytics purposes.
If `CONTACT_METADATA` event is used directly, then the value is not logged for reports

#### Parameters

| Key           | Type    | Required |
| ------------- | ------- | -------- |
| `ageRange`    | number  | yes      |
| `interaction` | boolean | yes      |
| `targetAge`   | number  | yes      |

### sendDetectGender
```javascript
eventTracking.sendDetectGender(params);
```

Information about the user, returned from computer vision, 3rd party services, or selected by a user in the UI
Note, this method will update the Contact Metadata but it will also log the values for analytics purposes.
If `CONTACT_METADATA` event is used directly, then the value is not logged for reports

#### Parameters

| Key           | Type    | Required | Description                                                                |
| ------------- | ------- | -------- | -------------------------------------------------------------------------- |
| `certainty`   | number  | yes      | The certainty of the mood, provided by computer vision                     |
| `gender`      | string  | yes      | Any of the following: `FEMALE`, `MALE`                                     |
| `interaction` | boolean | yes      | If the user provided this value or if it was detected from computer vision |
### sendDetectMood
```javascript
eventTracking.sendDetectMood(params);
```
Information about the user, return from computer vision or selected by a user in the UI
Note, this method will update the Contact Metadata but it will also log the values for analytics purposes.
If `CONTACT_METADATA` event is used directly, then the value is not logged for reports

#### Parameters

| Key         | Type   | Required | Description                                                                              |
| ----------- | ------ | -------- | ---------------------------------------------------------------------------------------- |
| `certainty` | number | yes      | The certainty of the mood, provided by computer vision                                   |
| `mood`      | string | yes      | Any of the following: `ANGRY`, `DISGUST` , `FEAR`, `HAPPY`, `SAD`, `SURPRISE`, `NEUTRAL` |

## Custom Event
```javascript
eventTracking.sendCustomEvent(params);
```

Used for tracking custom events outside the standard session event methods. Any parameter can be sent, and you have the availabilty of 5 string and 5 number parameters.

#### Event Parameters

| Key         | Type    | Description                                                       | Required |
| ----------- | ------- | ----------------------------------------------------------------- | -------- |
| eventType   | string  | Event type outside the standard event types (Example: TEST_EVENT) | yes      |
| interaction | boolean | If the event is triggered by a user                               | yes      |
| productId   | string  | Product id related to the event                                   | no       |
| categoryId  | string  | Category id related to the event                                  | no       |
| int1        | number  | Integer type field related to the event                           | no       |
| int2        | number  | Integer type field related to the event                           | no       |
| int3        | number  | Integer type field related to the event                           | no       |
| int4        | number  | Integer type field related to the event                           | no       |
| int5        | number  | Integer type field related to the event                           | no       |
| str1        | string  | String type field related to the event                            | no       |
| str2        | string  | String type field related to the event                            | no       |
| str3        | string  | String type field related to the event                            | no       |
| str4        | string  | String type field related to the event                            | no       |
| str5        | string  | String type field related to the event                            | no       |