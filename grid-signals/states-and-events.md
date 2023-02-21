# Session and Space States

You can fetch the latest states or subscribe to changes of the sessions and spaces

- [getSessionState](/grid-signals/states-and-events?id=getsessionstate)
- [getSpaceState](/grid-signals/states-and-events?id=getspacestate)
- [getSpaceStateRows](/grid-signals/states-and-events?id=getspacestaterows)
- [subscribeSessionState](/grid-signals/states-and-events?id=subscribesessionstate)
- [subscribeSessionEvent](/grid-signals/states-and-events?id=subscribesessionevent)
- [subscribeSessionEvent](/grid-signals/states-and-events?id=subscribespacestate)
- [subscribeSpaceEvent](/grid-signals/states-and-events?id=subscribespaceevent)

# getSessionState
Returns the current session-state as a promise.

<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
const sessionState = await gs().getSessionState();
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
const sessionState = await gs.getSessionState();
...
```
<!-- tabs:end -->

Response
```js
{
  CART: {
    [productId: string]: number;
  };
  SEARCH: string[];
}
```

# getSpaceState
Returns the current space-state as a promise.
<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
const spaceState = await gs().getSpaceState();
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
const spaceState = await gs.getSpaceState();
...
```
<!-- tabs:end -->

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

# getSpaceStateRows
Returns the latest space-state by session

<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
const spaceStateRows = await gs().getSpaceStateRows();
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
const spaceStateRows = await gs.getSpaceStateRows();
...
```
<!-- tabs:end -->


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

# subscribeSessionState
Subscribes to the latest session-state changes

<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
const sessionSubscription = await gs().subscribeSessionState((sessionState) => {
  console.log(sessionState);
});
...
sessionSubscription.stop(); // gracefully stop session subscription
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
...
const sessionSubscription = await gs.subscribeSessionState((sessionState) => {
  console.log(sessionState);
});
...
sessionSubscription.stop();
...
```
<!-- tabs:end -->


Session state data format
```js
{
  CART: {
    [productId: string]: number;
  };
  SEARCH: string[];
}
```


# subscribeSessionEvent
Subscribes to the latest session events

<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
const sessionSubscription = await gs().subscribeSessionEvent((sessionEvent) => {
  console.log(sessionEvent);
});
...
sessionSubscription.stop(); // gracefully stop session subscription
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
...
const sessionSubscription = await gs.subscribeSessionEvent((sessionEvent) => {
  console.log(sessionEvent);
});
...
sessionSubscription.stop();
...
```
<!-- tabs:end -->

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

# subscribeSpaceState
Subscribes the current application to a space-state.

<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
const spaceSubscription = await gs().subscribeSpaceState((spaceState) => {
  console.log(spaceState);
});
...
spaceSubscription.stop(); // gracefully stop session subscription
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
...
const spaceSubscription = await gs.subscribeSpaceState((spaceState) => {
  console.log(spaceState);
});
...
spaceSubscription.stop();
...
```
<!-- tabs:end -->

Space-state data format
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

# subscribeSpaceEvent
Subscribes to the latest specific space events

<!-- tabs:start -->
## **React**
```js
import { getInstance as gs } from '@ombori/grid-signals-react';
...
const spaceSubscription = await gs().subscribeSpaceEvent((spaceState) => {
  console.log(spaceState);
});
...
spaceSubscription.stop(); // gracefully stop session subscription
...
```

## **NodeJS or Javascript**
```js
import GridSignals from '@ombori/grid-signals';
...
const gs = new GridSignals();
await gs.init(<init-params>); // Check NodeJS App Integration page for init params reference
...
const spaceSubscription = await gs.subscribeSpaceEvent((spaceState) => {
  console.log(spaceState);
});
...
spaceSubscription.stop();
...
```
<!-- tabs:end -->

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
