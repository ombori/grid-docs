# Session and Space States

You can fetch the latest states or subscribe to changes of the sessions and spaces

- [getSessionState](/session-manager/states?id=getsessionstate)
- [getSpaceState](/session-manager/states?id=getspacestate)
- [subscribeSessionState](/session-manager/states?id=subscribesessionstate)
- [subscribeSpaceState](/session-manager/states?id=subscribespacestate)

## getSessionState

▸ `Const` **getSessionState**(): Promise<AxiosResponse<any, any\>\>

### Example

```js
import { states } from '@ombori/session-manager';
...

const currentSessionState = await states.getSessionState();
```

### Returns

Promise<AxiosResponse<any, any\>\>


## getSpaceState

▸ `Const` **getSpaceState**(`params`): Promise<AxiosResponse<any, any\>\>

### Parameters

| Key | Type | Description | Required | 
| :------ | :------ | :------ | :------ |
| `username` | string | browser id | yes |
| `password` | string | browser access key | yes |


### Example

```js
import { states } from '@ombori/session-manager';
...

const currentSessionState = await states.getSpaceState({
  password: 'XXXXXXXX-XXXX-XXXXX-XXXX-XXXXXXXXXXXX',
  username: 'XXXXXXXX-XXXX-XXXXX-XXXX-XXXXXXXXXXXX'
});
```

### Returns

Promise<AxiosResponse<any, any\>\>


## subscribeSessionState

▸ `Const` **subscribeSessionState**(`params`): Promise<Object\>

### Parameters

| Key | Type | Description | Required | 
| :------ | :------ | :------ | :------ |
| `username` | string | browser id | yes |
| `password` | string | browser access key | yes |

### Example

```js
import { states } from '@ombori/session-manager';
...

const onSessionStateEvent = (data) => alert(data);
const sessionState = await states.subscribeSessionState();
sessionState.subscribe(onSessionStateEvent);

...

// Gracefully stop state subscription
await sessionState.stop();
```

#### Returns

Promise<Object\>

___

## subscribeSpaceState

▸ `Const` **subscribeSpaceState**(`params`): Promise<Object\>

### Parameters

| Key | Type | Description | Required | 
| :------ | :------ | :------ | :------ |
| `username` | string | browser id | yes |
| `password` | string | browser access key | yes |

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

#### Returns

Promise<Object\>
