# Event Tracking
Standard Session Events are pre-defined methods that are common accross different types of apps within the Grid. It is created so that the same events will have the same payload so we can easily build reports from the collected analytics data.

## E-commerce Events
- [sendCartView](/session-manager/standard-session-events?id=e-commerce-events)
- [sendCartAdd](/session-manager/standard-session-events?id=sendcartadd)
- [sendCartRemove](/session-manager/standard-session-events?id=sendcartremove)
- [sendCartClear](/session-manager/standard-session-events?id=sendcartclear)
- [sendCategoryView](/session-manager/standard-session-events?id=sendcategoryview)
- [sendCheckout](/session-manager/standard-session-events?id=sendcheckout)
- [sendLookView](/session-manager/standard-session-events?id=sendlookview)
- [sendProductView](/session-manager/standard-session-events?id=sendproductview)
- [sendPurchase](/session-manager/standard-session-events?id=sendpurchase)

### sendCartView
▸ `Const` **sendCartView**(): Promise<void\>

Viewing the cart page

#### Returns

Promise<void\>

### sendCartAdd

▸ `Const` **sendCartAdd**(`params`): Promise<void\>

Adding a product to the cart

#### Parameters

| Key | Type | Description | Required |
| :------ | :------ | :------ | :------ |
| `productId` | string | Product primary id used in PIM | yes |
| `quantity` | number | Product quantity added into the cart | yes |

#### Returns

Promise<void\>

### sendCartClear

▸ `Const` **sendCartClear**(): Promise<void\>

Clearing the cart

#### Returns

Promise<void\>

### sendCartRemove

▸ `Const` **sendCartRemove**(`params`): Promise<void\>

Removing a product from the cart

#### Parameters

| Key | Type | Description | Required |
| :------ | :------ | :------ | :------ |
| `productId` | string | Product primary id used in PIM | yes |
| `quantity` | number | Product quantity removed from the cart | yes |

#### Returns

Promise<void\>

### sendCategoryView

▸ `Const` **sendCategoryView**(`params`): Promise<void\>

Browsing products under a category

#### Parameters

| Key | Type | Description |Required |
| :------ | :------ | :------ | :------ |
| `categoryId` | string | Category primary id used in PIM | yes |

#### Returns

Promise<void\>

### sendCheckout

▸ `Const` **sendCheckout**(): Promise<void\>

Checkout step before payment

#### Returns

Promise<void\>

### sendLookView

▸ `Const` **sendLookView**(`params`): Promise<void\>

Viewing a specific fashion look, which is an array of products

#### Parameters

| Key | Type | Required |
| :------ | :------ | :------ |
| `lookId` | string | yes |

#### Returns

Promise<void\>

### sendProductView

▸ `Const` **sendProductView**(`params`): Promise<void\>

Viewing a specific product page

#### Parameters

| Key | Type | Description | Required |
| :------ | :------ | :------ | :------ |
| `productId` | string | Product primary id used in PIM | yes |

#### Returns

Promise<void\>

### sendPurchase

▸ `Const` **sendPurchase**(`params`): Promise<void\>

Payment success

#### Parameters

| Key | Type | Required |
| :------ | :------ | :------ |
| `coupon` | string | no |
| `currencyCode` | string | yes |
| `revenue` | number | yes |
| `shipping` | number | yes |
| `tax` | number | yes |
| `transactionId` | string | yes |

#### Returns

Promise<void\>

## Contact Events

- [sendContactIdentify](/session-manager/standard-session-events?id=sendcontactidentify)
- [sendContactMetadata](/session-manager/standard-session-events?id=sendcontactmetadata)
- [sendDetectAge](/session-manager/standard-session-events?id=senddetectage)
- [sendDetectGender](/session-manager/standard-session-events?id=senddetectgender)
- [sendDetectMood](/session-manager/standard-session-events?id=senddetectmood)

### sendContactIdentify

▸ `Const` **sendContactIdentify**(`params`): Promise<void\>

Identifying the customer based on a known identifyer

#### Parameters

| Key | Type | Required |
| :------ | :------ | :------ |
| `contact` | string | yes |
| `contactType` | "PHONE" \| "EMAIL" \| "CLIENT\_ID" | yes |
| `interaction` | boolean | yes |

#### Returns

Promise<void\>

### sendContactMetadata

▸ `Const` **sendContactMetadata**(`params`): Promise<void\>

Identifying the customer based on a known identifyer

#### Parameters

| Key | Type | Required |
| :------ | :------ | :------ |
| `interaction` | boolean | yes |
| `str1` | string | yes |
| `str2` | string | yes |

#### Returns

Promise<void\>

### sendDetectAge

▸ `Const` **sendDetectAge**(`params`): Promise<void\>

Information about the user, returned from computer vision, 3rd party services, or selected by a user in the UI
Note, the below method will update the Contact Metadata but it will also log the values for analytics purposes.
If CONTACT_METADATA event is used directly, then the value is not logged for reports

#### Parameters

| Key | Type | Required |
| :------ | :------ | :------ | 
| `ageRange` | number | yes |
| `interaction` | boolean | yes |
| `targetAge` | number | yes |

#### Returns

Promise<void\>


### sendDetectGender

▸ `Const` **sendDetectGender**(`params`): Promise<void\>

Information about the user, returned from computer vision, 3rd party services, or selected by a user in the UI
Note, the below method will update the Contact Metadata but it will also log the values for analytics purposes.
If CONTACT_METADATA event is used directly, then the value is not logged for reports

#### Parameters

| Key | Type | Required |
| :------ | :------ | :------ | 
| `certainty` | number | yes |
| `gender` | "FEMALE" \| "MALE" | yes|
| `interaction` | boolean | yes |

#### Returns

Promise<void\>

### sendDetectMood

▸ `Const` **sendDetectMood**(`params`): Promise<void\>

Information about the user, return from computer vision or selected by a user in the UI
Note, the below method will update the Contact Metadata but it will also log the values for analytics purposes.
If CONTACT_METADATA event is used directly, then the value is not logged for reports

#### Parameters

| Key | Type | Required |
| :------ | :------ | :------ | 
| `certainty` | number | yes |
| `mood` | "ANGRY" \| "DISGUST" \| "FEAR" \| "HAPPY" \| "SAD" \| "SURPRISE" \| "NEUTRAL" | yes |

#### Returns

Promise<void\>

## Generic Events

- [sendAppStart](/session-manager/standard-session-events?id=sendappstart)
- [sendContentView](/session-manager/standard-session-events?id=sendcontentview)
- [sendRating](/session-manager/standard-session-events?id=sendrating)
- [sendSearch](/session-manager/standard-session-events?id=sendsearch)
- [sendSearchClear](/session-manager/standard-session-events?id=sendsearchclear)

### sendAppStart

▸ `Const` **sendAppStart**(): Promise<void\>

This function is executed by default when [init](/session-manager/main-functions?id=init) is invoked.

#### Returns

Promise<void\>

### sendContentView

▸ `Const` **sendContentView**(`params`): Promise<void\>

Viewing a generic piece of content, equivalent to a "pageview" in old school web analytics

#### Parameters

| Name | Type | Required | 
| :------ | :------ | :------ |
| `localizedTitle?` | string | no |
| `title` | string  | yes |
| `url?` | string  | no |

#### Returns

Promise<void\>

### sendRating

▸ `Const` **sendRating**(`params`): Promise<void\>

User's rate of the experience

#### Parameters

| Name | Type | Required | 
| :------ | :------ | :------ |
| `comment` | string | yes |
| `interactionDelay` | number | yes |
| `rating` | 1 \| 2 \| 3 \| 4 \| 5 | yes |

#### Returns

Promise<void\>

### sendSearch

▸ `Const` **sendSearch**(`params`): Promise<void\>

Searching a product, category, or anything in the app

#### Parameters

| Name | Type |
| :------ | :------ |
| `searchQueryString` | string |

#### Returns

Promise<void\>

### sendSearchClear

▸ `Const` **sendSearchClear**(): Promise<void\>

Searching a product, category, or anything in the app

#### Returns

Promise<void\>

## Custom Event

- [trackEvent](/session-manager/event-tracking?id=custom-event)

▸ `Const` **sendCustomEvent**(`eventParams`): Promise<void\>

Used for tracking custom  events outside the standard session event methods.

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
#### Returns

Promise<void\>

___