# Integrating Grid Signals on React Apps 

!> Grid Signals is currently in pre-release. Breaking changes are not likely but can still occur before production release in March

This page describes how you can integrate your React-based App to Grid Signals.

#### Functions
- [useGridSignals](grid-signals/react-app-integration?id=useGridSignals)
- [useGridSignalsWithExternalParams](grid-signals/react-app-integration?id=createsession)
- [getInstance](/grid-signals/react-app-integration?id=getinstance)
- [getInstanceProps](/grid-signals/react-app-integration?id=getinstanceprops)
- [createSession](/grid-signals/react-app-integration?id=createsession)

#### States and Events
- [Event Tracking](grid-signals/tracking-events)
- [States and Events Subscription](grid-signals/states-and-events)


## useGridSignals
Use this hook if your app is built from `omg app create` template, or is using `@ombori/ga-settings`.

It initializes the Grid Signals instance using the application settings. Under the hood, it uses `@ombori/ga-settings` to automatically get the required Grid Signals parameters for initialization.

You can only start invoking any other functions when Grid Signals is ready.

#### Usage

```js
import React from 'react';
import { useGridSignals, getInstance as gs } from '@ombori/grid-signals-react';
const App = () => {
  const isReady = useGridSignals();
  if (!isReady) {
    return <div>Initializing App</div>;
  }
  return <MainPage />;
}
```

Ideally, you don't need to override the parameters when using this function. However, we provide the ability to override the [Grid Signals Init Parameters](grid-signals/react-app-integration?id=grid-signals-init-parameters) for flexibility.


```js
const isReady = useGridSignals({
  environment: 'TEST_ENV',
  ...<other valid parameters you want to override>,
});
```

## useGridSignalsWithExternalParams
Use this hook if your app is not using `@ombori/ga-settings`.

It initializes the Grid Signals instance with the required [Init Parameters](grid-signals/react-app-integration?id=grid-signals-init-parameters).

#### Usage
```js
import React from 'react';
import { useGridSignalsWithExternalParams } from '@ombori/grid-signals-react';

const App = () => {
  const isReady = useGridSignalsWithExternalParams({
    deviceId: 'XXXXXXXXXXXXXXXXXXXXXXXX',
    installationId: 'XXXXXXXXXXXXXXXXXXXXXXXX',
    spaceId: 'XXXXXXXXXXXXXXXXXXXXXXXX',
    tenantId: 'XXXXXXXXXXXXXXXXXXXXXXXX',
    appVersion: 'XXXXXXXXXXXXXXXXXXXXXXXX',
    appId: 'XXXXXXXXXXXXXXXXXXXXXXXX',
    environment: 'PROD',
    dataResidency: 'EU',
    country: 'SE',
    installationVersion: 'XXXXXXXXXXXXXXXXXXXXXXXX',
    username: 'XXXX',
    password: 'XXXX',
  });

  if (!isReady) {
    return <div>Initializing App</div>;
  }

  return <MainPage />;
}
```

## getInstanceProps
This will return the instance object of the session. Ideally your don't need to get the instance props. However, we added it for flexibility.

Usage
```js
import { getInstance as gs } from '@ombori/grid-signals-react';

...
  gs().getInstanceProps();
...
```

#### Returns

These are the instance properties that are returned from the `getInstance()` method.

| Key                 | Type   | Description                                                                                   |
| ------------------- | ------ | --------------------------------------------------------------------------------------------- |
| tenantId            | string | Tenant id in the Grid Console                                                                 |
| sessionId           | string | Grid Session instance-id                                                                      |
| environment         | string | Application environment                                                                       |
| dataResidency       | string | The region where to store the data                                                            |
| country             | string | Tenant base country (Abbrev.)                                                                 |
| spaceId             | string | The id of the Space where the device or any entity is located                                 |
| appId               | string | The id of the gridapp which is running on a device                                            |
| appVersion          | string | List of Product Type IDs applicable to this product as a reference from ProductTypes Database |
| installationId      | string | The id of the installation in Grid Console                                                    |
| installationVersion | string | Build id of the installation                                                                  |
| deviceId            | string | Id of the device in the console. If deviceId is not passed, virtual deviceId is created       |
| clientId            | string | Client id of the requestor. clientId is same as deviceId for registered devices in console    |
| clientCreated       | string | Date when the client id is created                                                            |
| clientUserAgent     | string | Requestor user agent                                                                          |
| locationAccuracy    | number | Geographic coordinates accuracy                                                               |
| latitude            | number | Geographic latitude of the device or requestor                                                |
| longitude           | number | Geographic longitude of the device or requestor                                               |
| lastActivity        | string | Date string of the last invoked function                                                             |


## createSession
Starts a new session. You should call this method every time a new user starts interacting with the application.

Usage
```js
import { getInstance as gs } from '@ombori/grid-signals-react';

...
  gs().createSession();
...
```

## Grid Signals Init Parameters

| Key                 | Type   | Description                                                                                   | Required | Options                       |
| ------------------- | ------ | --------------------------------------------------------------------------------------------- | -------- | ----------------------------- |
| tenantId            | string | Tenant id in the Grid Console                                                                 | yes      |                               |
| environment         | string | Application environment                                                                       | yes      |                               |
| dataResidency       | string | The region where to store the data                                                            | yes      | "EU", "UAE", "IN", "US", "AU" |
| country             | string | Tenant base country (Abbrev.)                                                                 | yes      |                               |
| spaceId             | string | The id of the Space where the device or any entity is located                                 | yes      |                               |
| appId               | string | The id of the gridapp which is running on a device                                            | yes      |                               |
| appVersion          | string | List of Product Type IDs applicable to this product as a reference from ProductTypes Database | yes      |                               |
| installationId      | string | The id of the installation in Grid Console                                                    | yes      |                               |
| installationVersion | string | Build id of the installation                                                                  | yes      |                               |
| deviceId            | string | Id of the device in the console. If deviceId is not passed, virtual deviceId is created       | no       |                               |
| clientUserAgent     | string | Requestor user agent                                                                          | yes      |                               |
| locationAccuracy    | number | Geographic coordinates accuracy                                                               | no       |                               |
| latitude            | number | Geographic latitude of the device or requestor                                                | no       | -90 to 90                     |
| longitude           | number | Geographic longitude of the device or requestor                                               | no       | -180 to 180                   |
| username            | string | Credentials used when subscribing to session or space state or events                         | no       |                               |
| password            | string | Credentials used when subscribing to session or space state or events                         | no       |                               |

## Event Tracking
See [Event Tracking](grid-signals/tracking-events) page for more details.

## States and Events Subscription
See [States and Events Subscription](grid-signals/states-and-events) page for more details.
