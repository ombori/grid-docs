# Integrating Grid Signals on NodeJS and other Javascript libraries

!> Grid Signals is currently in pre-release. Breaking changes are not likely but can still occur before production release

This page describes how you can integrate your NodeJS or Non-react JavaScript-based gridapps.

#### Functions
- [init](grid-signals/nodejs-integration?id=init)

#### States and Events
- [Event Tracking](grid-signals/tracking-events)
- [States and Events Subscription](grid-signals/states-and-events)

## init
Used to initialize the Grid Signals instance with the required [Init Parameters](grid-signals/nodejs-integration?id=grid-signals-init-parameters).


```js
import GridSignals from '@ombori/grid-signals';

...
const gs = new GridSignals();
await gs.init(params)
...
```

#### Usage
```js
import GridSignals from '@ombori/grid-signals';

...

const gs = new GridSignals();
await gs.init({
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
  accessId: 'XXXX',
  accessToken: 'XXXX',
});

await gs.sendCustomEvent({
  eventType: 'RECYCLE',
  interaction: true,
  str1: 'bottles', // unit
  int1: 5, // quantity
});

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
| accessId            | string | Credentials used when subscribing to session or space state or events                         | no       |                               |
| accessToken         | string | Credentials used when subscribing to session or space state or events                         | no       |                               |

## Event Tracking
See [Event Tracking](grid-signals/tracking-events) page for more details.

## States and Events Subscription
See [States and Events Subscription](grid-signals/states-and-events) page for more details.
