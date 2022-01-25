# Event Tracking

!> Grid Signals is currently in pre-release. Breaking changes are not likely but can still occur before production release in March

In Grid Signals, we classify events to be tracked as:

#### Standard Events
predefined functions and events that are common across different types of apps within the Grid. It is created so that the same events will have the same payload, then, we can easily build reports from the collected analytics data

When tracking user identity, `identifyContact` and `sendContactMetadata` should be used.

- [detectAge](/grid-signals/tracking-events?id=detectage)
- [detectGender](/grid-signals/tracking-events?id=detectgender)
- [detectMood](/grid-signals/tracking-events?id=detectmood)
- [identifyContact](/grid-signals/tracking-events?id=identifycontact)
- [sendCartAdd](/grid-signals/tracking-events?id=sendcartadd)
- [sendCartClear](/grid-signals/tracking-events?id=sendcartclear)
- [sendCartRemove](/grid-signals/tracking-events?id=sendcartremove)
- [sendCartView](/grid-signals/tracking-events?id=sendcartview)
- [sendCategoryView](/grid-signals/tracking-events?id=sendcategoryview)
- [sendCheckout](/grid-signals/tracking-events?id=sendcheckout)
- [sendContactMetadata](/grid-signals/tracking-events?id=sendcontactmetadata)
- [sendContentView](/grid-signals/tracking-events?id=sendcontentview)
- [sendFeedback](/grid-signals/tracking-events?id=sendfeedback)
- [sendLookView](/grid-signals/tracking-events?id=sendlookview)
- [sendProductView](/grid-signals/tracking-events?id=sendproductview)
- [sendPurchase](/grid-signals/tracking-events?id=sendpurchase)
- [sendRating](/grid-signals/tracking-events?id=sendrating)
- [sendSearch](/grid-signals/tracking-events?id=sendsearch)
- [sendSearchClear](/grid-signals/tracking-events?id=sendsearchclear)

#### Custom Events
any events and parameters based on you needs
- [sendCustomEvent](/grid-signals/tracking-events?id=sendCustomEvent)

Make sure you only invoke function events *after* Grid Signals is initialized.


# detectAge
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().detectAge(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.detectAge(params);
...
```
<!-- tabs:end -->

Information about the user, returned from computer vision, 3rd party services, or selected by a user in the UI
Note, this method will update the Contact Metadata but it will also log the values for analytics purposes.
If `CONTACT_METADATA` event is used directly, then the value is not logged for reports

#### Parameters

| Key           | Type    | Required |
| ------------- | ------- | -------- |
| `ageRange`    | number  | yes      |
| `interaction` | boolean | yes      |
| `targetAge`   | number  | yes      |

# detectGender
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().detectGender(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.detectGender(params);
...
```
<!-- tabs:end -->

Information about the user, returned from computer vision, 3rd party services, or selected by a user in the UI
Note, this method will update the Contact Metadata but it will also log the values for analytics purposes.
If `CONTACT_METADATA` event is used directly, then the value is not logged for reports

#### Parameters

| Key           | Type    | Required | Description                                                                |
| ------------- | ------- | -------- | -------------------------------------------------------------------------- |
| `certainty`   | number  | yes      | The certainty of the mood, provided by computer vision                     |
| `gender`      | string  | yes      | Any of the following: `FEMALE`, `MALE`                                     |
| `interaction` | boolean | yes      | If the user provided this value or if it was detected from computer vision |

# detectMood
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().detectMood(params);
...
```


## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.detectMood(params);
...
```
<!-- tabs:end -->
Information about the user, return from computer vision or selected by a user in the UI
Note, this method will update the Contact Metadata but it will also log the values for analytics purposes.
If `CONTACT_METADATA` event is used directly, then the value is not logged for reports

#### Parameters

| Key         | Type   | Required | Description                                                                              |
| ----------- | ------ | -------- | ---------------------------------------------------------------------------------------- |
| `certainty` | number | yes      | The certainty of the mood, provided by computer vision                                   |
| `mood`      | string | yes      | Any of the following: `ANGRY`, `DISGUST` , `FEAR`, `HAPPY`, `SAD`, `SURPRISE`, `NEUTRAL` |

# identifyContact
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().identifyContact(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.identifyContact(params);
...
```
<!-- tabs:end -->

Identifying the customer based on a known identifier

#### Parameters

| Key           | Type    | Required | Description                                        |
| ------------- | ------- | -------- | -------------------------------------------------- |
| `contactType` | STRING  | yes      | Provide any of `PHONE`, `EMAIL` and `CLIENT_ID`    |
| `contact`     | string  | yes      | Enter the value of `contactType`                   |
| `interaction` | boolean | yes      | Whether the event was triggered by the user or not |

# sendCartAdd
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendCartAdd(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendCartAdd(params);
...
```
<!-- tabs:end -->

Adding a product to the cart

#### Parameters

| Key         | Type   | Description                          | Required |
| ----------- | ------ | ------------------------------------ | -------- |
| `productId` | string | Product primary id used in PIM       | yes      |
| `quantity`  | number | Product quantity added into the cart | yes      |

# sendCartClear
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendCartClear();
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendCartClear();
...
```
<!-- tabs:end -->

Clear the cart

# sendCartRemove
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendCartRemove(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendCartRemove(params);
...
```
<!-- tabs:end -->

Remove a product from the cart

#### Parameters

| Key         | Type   | Description                          | Required |
| ----------- | ------ | ------------------------------------ | -------- |
| `productId` | string | Product primary id used in PIM       | yes      |
| `quantity`  | number | Product quantity added into the cart | yes      |


# sendCartView
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendCartView();
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendCartView();
...
```
<!-- tabs:end -->

View the cart page



# sendCategoryView
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendCategoryView(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendCategoryView(params);
...
```
<!-- tabs:end -->

Browse a category's page

#### Parameters

| Key          | Type   | Description                     | Required |
| ------------ | ------ | ------------------------------- | -------- |
| `categoryId` | string | Category primary id used in PIM | yes      |

# sendCheckout
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendCheckout();
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendCheckout();
...
```
<!-- tabs:end -->

Checkout step before payment

# sendContactMetadata
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendContactMetadata(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendContactMetadata(params);
...
```
<!-- tabs:end -->

Identifying the customer based on a known identifier.

#### Parameters

| Key           | Type    | Required | Description                                        |
| ------------- | ------- | -------- | -------------------------------------------------- |
| `interaction` | boolean | yes      | Whether the event was triggered by the user or not |
| `str1`        | string  | yes      | Provide any of `PHONE`, `EMAIL` and `CLIENT_ID`    |
| `str2`        | string  | yes      | The value of the `str1` field                      |

# sendContentView
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendContactMetadata(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendContactMetadata(params);
...
```
<!-- tabs:end -->

View a generic piece of content, equivalent to a "pageview" in old school web analytics

#### Parameters

| Key              | Type   | Required |
| ---------------- | ------ | -------- |
| `localizedTitle` | string | no       |
| `title`          | string | yes      |
| `url`            | string | no       |

# sendFeedback
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendFeedback(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendFeedback(params);
...
```
<!-- tabs:end -->

Send user's feedback on the experience

#### Parameters

| Key                | Type                  | Required |
| ------------------ | --------------------- | -------- |
| `feedback`         | string                | yes      |
| `rating`           | 1 \| 2 \| 3 \| 4 \| 5 | no       |

# sendLookView
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendLookView(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendLookView(params);
...
```
<!-- tabs:end -->


Viewing a specific fashion look, which is an array of products

#### Parameters

| Key      | Type   | Required |
| -------- | ------ | -------- |
| `lookId` | string | yes      |

# sendProductView
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendProductView(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendProductView(params);
...
```
<!-- tabs:end -->

View a specific product page

#### Parameters

| Key         | Type   | Description                    | Required |
| ----------- | ------ | ------------------------------ | -------- |
| `productId` | string | Product primary id used in PIM | yes      |

# sendPurchase
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendPurchase(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendPurchase(params);
...
```
<!-- tabs:end -->

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

# sendRating
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendRating(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendRating(params);
...
```
<!-- tabs:end -->

The user's rating of the experience

#### Parameters

| Key                | Type                  | Required |
| ------------------ | --------------------- | -------- |
| `comment`          | string                | yes      |
| `interactionDelay` | number                | no       |
| `rating`           | 1 \| 2 \| 3 \| 4 \| 5 | yes      |

# sendSearch
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendSearch(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendSearch(params);
...
```
<!-- tabs:end -->

Searching a product, category, or anything in the app

#### Parameters

| Key                | Type                  | Required |
| ------------------ | --------------------- | -------- |
| `searchQueryString`| string                | yes      |


# sendSearchClear
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendSearchClear();
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendSearchClear();
...
```
<!-- tabs:end -->

Searching a product, category, or anything in the app

# sendCustomEvent
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
gs().sendCustomEvent(params);
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
await gs.sendCustomEvent(params);
...
```
<!-- tabs:end -->

Used for tracking custom events outside the standard session event methods. Any parameter can be sent, and you have the availabilty of 5 string and 5 number parameters.

#### Parameters

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
