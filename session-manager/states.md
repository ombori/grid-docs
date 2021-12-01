# Session and Space States

You can fetch the latest states or subscribe to changes of the sessions and spaces

- [getSessionState](/session-manager/states?id=getsessionstate)
- [getSpaceState](/session-manager/states?id=getspacestate)
- [getSpaceStateRows](/session-manager/states?id=getspacestaterows)
- [createSessionStateSubscription](/session-manager/states?id=createsessionstatesubscription)
- [createSessionEventSubscription](/session-manager/states?id=createsessioneventsubscription)
- [createSpaceStateSubscription](/session-manager/states?id=createspacestatesubscription)
- [createSpaceEventSubscription](/session-manager/states?id=createspaceeventsubscription)

## getSessionState

Returns the current session state as a promise.

```js
import { states } from '@ombori/session-manager';
...

const currentSessionState = await states.getSessionState();
```

Response
```js
{
  CART: {
    [productId: string]: number;
  };
  SEARCH: string[];
}
```

## getSpaceState
Returns the current space state as a promise.

```js
import { states } from '@ombori/session-manager';
...

const currentSessionState = await states.getSpaceState({
  password: 'XXXXXXXX-XXXX-XXXXX-XXXX-XXXXXXXXXXXX',
  username: 'XXXXXXXX-XXXX-XXXXX-XXXX-XXXXXXXXXXXX'
});
```

Response
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
Returns the latest space state by session

```js
import { states } from '@ombori/session-manager';
...

const currentSessionState = await states.getSpaceStateRows({
  password: 'XXXXXXXX-XXXX-XXXXX-XXXX-XXXXXXXXXXXX',
  username: 'XXXXXXXX-XXXX-XXXXX-XXXX-XXXXXXXXXXXX'
});
```

Response
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
Subscribes to the latest session state changes

```js
import { states } from '@ombori/session-manager';
...
const onSessionState = (data) => alert(data);
const sessionState = await states.createSessionStateSubscription();
sessionState.subscribe(onSessionState);


// Gracefully stop state subscription
await sessionState.stop();
```

Session state data format
```js
{
  CART: {
    [productId: string]: number;
  };
  SEARCH: string[];
}
```


## createSessionEventSubscription
Subscribes to the latest session events

```js
import { states } from '@ombori/session-manager';
...
const onSessionEvent = (data) => alert(data);
const sessionEvent = await states.createSessionEventSubscription();
sessionEvent.subscribe(onSessionEvent);
...
// Gracefully stop state subscription
await sessionEvent.stop();
```

Session event data format
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
Subscribes the current application to a space state.

```js
import { states } from '@ombori/session-manager';
...

const onSpaceEvent = (data) => alert(data);
const spaceState = await states.createSpaceStateSubscription();
spaceState.subscribe(onSpaceEvent);

...

// Gracefully stop state subscription
await spaceState.stop();
```
#### Parameters

| Key        | Type   | Description        | Required |
| :--------- | :----- | :----------------- | :------- |
| `username` | string | browser id         | yes      |
| `password` | string | browser access key | yes      |

Space state data format
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
    expiry: 1800;
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
Subscribes to the latest specific space events

```js
import { states } from '@ombori/session-manager';
...

const onSpaceEvent = (data) => alert(data);
const spaceEvent = await states.createSpaceEventSubscription();
spaceEvent.subscribe(onSpaceEvent);
...

// Gracefully stop the subscription
await spaceEvent.stop();
```
#### Parameters

| Key        | Type   | Description        | Required |
| :--------- | :----- | :----------------- | :------- |
| `username` | string | browser id         | yes      |
| `password` | string | browser access key | yes      |

Space event data format
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
