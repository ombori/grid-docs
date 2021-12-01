# Session and Space States

You can fetch the latest states or subscribe to changes of the sessions and spaces

- [getSessionState](/session-manager/states?id=getsessionstate)
- [getSpaceState](/session-manager/states?id=getspacestate)
- [subscribeSessionState](/session-manager/states?id=subscribesessionstate)
- [subscribeSpaceState](/session-manager/states?id=subscribespacestate)

## getSessionState

Returns the current session state as a promise.

```js
import { states } from '@ombori/session-manager';
...

const currentSessionState = await states.getSessionState();
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


### Parameters

| Key        | Type   | Description        | Required |
| :--------- | :----- | :----------------- | :------- |
| `username` | string | browser id         | yes      |
| `password` | string | browser access key | yes      |


## subscribeSessionState

Subscribes the application to a session state.

```js
import { states } from '@ombori/session-manager';
...

const onSessionStateEvent = (data) => alert(data);
const sessionState = await states.subscribeSessionState();
sessionState.subscribe(onSessionStateEvent);

// Gracefully stop state subscription
await sessionState.stop();
```


### Parameters

| Key        | Type   | Description        | Required |
| :--------- | :----- | :----------------- | :------- |
| `username` | string | browser id         | yes      |
| `password` | string | browser access key | yes      |


## subscribeSpaceState
Subscribes the current application to a space state.

```js
import { states } from '@ombori/session-manager';
...

const onSpaceSateEvent = (data) => alert(data);
const spaceState = await states.subscribeSpaceState();
spaceState.subscribe(onSpaceSateEvent);

...

// Gracefully stop state subscription
await spaceState.stop();
```
### Parameters

| Key        | Type   | Description        | Required |
| :--------- | :----- | :----------------- | :------- |
| `username` | string | browser id         | yes      |
| `password` | string | browser access key | yes      |

