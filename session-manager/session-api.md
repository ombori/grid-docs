# Grid Session APIs

When integrating Grid Session Manager on server-side, you may want to just directly send events to the Grid Session API.

- [sendClient](/session-manager/session-api?id=sendclient)
- [sendSession](/session-manager/session-api?id=sendsession)
- [sendEvent](/session-manager/session-api?id=sendevent)
- [getSessionState](/session-manager/session-api?id=getsessionstate)
- [getSpaceState](/session-manager/session-api?id=getspacestate)
- [getSpaceStateRows](/session-manager/session-api?id=getspacestaterows)
- [createSessionStateSubscription](/session-manager/session-api?id=createsessionstatesubscription)
- [createSessionEventSubscription](/session-manager/session-api?id=createsessioneventsubscription)
- [createSpaceStateSubscription](/session-manager/session-api?id=createspacestatesubscription)
- [createSpaceEventSubscription](/session-manager/session-api?id=createspaceeventsubscription)

## sendClient
Send device client information

### Parameters

| Key                      | Type   | Required |
| :----------------------- | :----- | :------- |
| `tenantId`               | string | yes      |
| `clientId`               | string | yes      |
| `clientCreated`          | string | yes      |
| `clientUserAgent`        | number | yes      |
| `dataResidency`          | string | yes      |
| `country`                | string | yes      |
| `locationAccuracy`       | number | no       |
| `latitude`               | number | no       |
| `longitude`              | number | no       |
| `clientScreenWidth`      | number | no       |
| `clientScreenHeight`     | number | no       |
| `clientScreenColorDepth` | number | no       |
| `clientScreenPixelDepth` | number | no       |

### Returns

Promise<void\>

## sendSession
Send new session information

### Parameters

| Key                   | Type   | Required |
| :-------------------- | :----- | :------- |
| `tenantId`            | string | yes      |
| `sessionId`           | string | yes      |
| `sessionCreated`      | string | yes      |
| `environment`         | number | yes      |
| `dataResidency`       | string | yes      |
| `country`             | string | yes      |
| `spaceId`             | string | yes      |
| `appId`               | string | yes      |
| `appVersion`          | string | yes      |
| `installationId`      | string | yes      |
| `installationVersion` | string | yes      |
| `deviceId`            | string | yes      |
| `clientId`            | string | yes      |
| `locationAccuracy`    | number | no       |
| `latitude`            | number | no       |
| `longitude`           | number | no       |

### Returns

Promise<void\>

## sendEvent
Send session events

### Parameters

| Key             | Type    | Required |
| :-------------- | :------ | :------- |
| `tenantId`      | string  | yes      |
| `eventTime`     | string  | yes      |
| `dataResidency` | string  | yes      |
| `sessionId`     | number  | yes      |
| `clientId`      | string  | yes      |
| `eventType`     | string  | yes      |
| `interaction`   | boolean | no       |
| `productId`     | string  | no       |
| `categoryId`    | string  | no       |
| `int1`          | number  | no       |
| `int2`          | number  | no       |
| `int3`          | number  | no       |
| `int4`          | number  | no       |
| `int5`          | number  | no       |
| `str1`          | string  | no       |
| `str2`          | string  | no       |
| `str3`          | string  | no       |
| `str4`          | string  | no       |
| `str5`          | string  | no       |
### Returns

Promise<void/>

## getSessionState
Get session state

#### Parameters

| Key             | Type   | Description                      | Required |
| :-------------- | :----- | :------------------------------- | :------- |
| `tenantId`      | string | Tenant id in console             | yes      |
| `sessionId`     | string | Session id                       | yes      |
| `dataResidency` | string | Tenant data residency in console | yes      |

#### Returns

Promise<GetSessionStateResponse\>

#### GetSessionStateResponse

```js
  session: {
    CART: {
      [productId: string]: number;
    };
    SEARCH: string[];
  }
``` 

## getSpaceState
Get space state based on sessionId

### Parameters

| Key             | Type   | Description                      | Required |
| :-------------- | :----- | :------------------------------- | :------- |
| `username`      | string | Browser id                       | yes      |
| `password`      | string | Browser access key               | yes      |
| `tenantId`      | string | Tenant id in console             | yes      |
| `sessionId`     | string | Session id                       | yes      |
| `dataResidency` | string | Tenant data residency in console | yes      |

### Returns

Promise<GetSpaceStateResponse>

#### GetSpaceStateResponse

```js
{
  RATING: {
    type: string;
    value: {
      min: number;
      max: number;
      mean: number;
      length: number;
    },
    expiry: number;
    created: string;
    updated: string;
  },
  CART: {
    [productId: string]: {
      quantity: number;
      contacts: number;
    };
  };
}
``` 


## getSpaceStateRows
Get space state from multiple sessions based on session id
### Parameters

| Key             | Type   | Description                      | Required |
| :-------------- | :----- | :------------------------------- | :------- |
| `username`      | string | Browser id                       | yes      |
| `password`      | string | Browser access key               | yes      |
| `tenantId`      | string | Tenant id in console             | yes      |
| `sessionId`     | string | Session id                       | yes      |
| `dataResidency` | string | Tenant data residency in console | yes      |

### Returns

Promise<GetSpaceStateRowsResponse>

#### GetSpaceStateRowsResponse

```js
{
  RATING: {
    [sessionId: string]: {
      value: number;
      expiry: number;
      updated: string;
    };
  },
  CART: {
    [sessionId: string]: {
      expiry: string;
      updated: string;
      value: {
        [productId: string]: number;
      };
    };
  };
}
``` 

## createSessionStateSubscription
Create session state subscription

### Parameters

| Name            | Type   |
| :-------------- | :----- |
| `sessionId`     | string |
| `dataResidency` | string |

### Returns

```js
{
  subscribe(callbackFn<SubscribeStateResponse>),
  stop,
}
```

#### SubscribeStateResponse
```js
{
  CART: {
    [productId: string]: number;
  };
  SEARCH: string[];
}
```

## createSessionEventSubscription
Create session event subscription

### Parameters

| Name            | Type   |
| :-------------- | :----- |
| `sessionId`     | string |
| `dataResidency` | string |
### Returns

```js
{
  subscribe(callbackFn<CreateEventSubscriptionResponse>),
  stop,
}
```

#### CreateEventSubscriptionResponse

```js
{
  captureId: string;
  clientId: string;
  dataResidency: string;
  eventTime: string;
  eventType: string;
  interaction: boolean;
  ip: string;
  productId: string;
  sessionId: string;
  tenantId: string;
  int1?: number;
  int2?: number;
  int3?: number;
  int4?: number;
  int5?: number;
  str1?: string;
  str2?: string;
  str3?: string;
  str4?: string;
  str5?: string;
}
``` 


## createSpaceStateSubscription
Create space state subscription

### Parameters

| Name            | Type   |
| :-------------- | :----- |
| `username`      | string |
| `password`      | string |
| `spaceId`       | string |
| `dataResidency` | string |

### Returns

```js
{
  subscribe(callbackFn<CreateSpaceStateSubscriptionResponse>),
  stop,
}
```

#### CreateSpaceStateSubscriptionResponse
```js
{
  RATING: {
    type: string;
    value: {
      min: number;
      max: number;
      mean: number;
      length: number;
    },
    expiry: number;
    created: string;
    updated: string;
  },
  CART: {
    [productId: string]: {
      quantity: number;
      contacts: number;
    };
  };
}
```

## createSpaceEventSubscription
Create space event subscription

### Parameters

| Name            | Type   |
| :-------------- | :----- |
| `username`      | string |
| `password`      | string |
| `spaceId`       | string |
| `dataResidency` | string |

### Returns

```js
{
  subscribe(callbackFn<CreateEventSubscriptionResponse>),
  stop,
}
```

#### CreateEventSubscriptionResponse

```js
{
  captureId: string;
  clientId: string;
  dataResidency: string;
  eventTime: string;
  eventType: string;
  interaction: boolean;
  ip: string;
  productId: string;
  sessionId: string;
  tenantId: string;
  int1?: number;
  int2?: number;
  int3?: number;
  int4?: number;
  int5?: number;
  str1?: string;
  str2?: string;
  str3?: string;
  str4?: string;
  str5?: string;
}
``` 