# Getting Started

!> Grid Signals is currently in pre-release. Breaking changes are not likely but can still occur before production release in March

Install the `Grid Signals library` to any of your applications.

## Set-up
#### React
```js
npm install @ombori/grid-signals-react
or
yarn add @ombori/grid-signals-react
```

#### Javascript
NodeJS and other client-side javascript libraries 
```js
npm install @ombori/grid-signals
or
yarn add @ombori/grid-signals
```

#### Notes
- `@ombori/grid-signals-react` is a package with `@ombori/grid-signals` and `@ombori/ga-settings` as dependencies, built for easier initialization and better support for React-based applications. Everything that you can import from `@ombori/grid-signals` is also in `@ombori/grid-signals-react`.
- You can use `@ombori/grid-signals` package for other JS libraries or server-side applications.

## Basic Usage

#### Example in React:
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

const MainPage = () => {
  React.useEffect(() => {
    gs().sendContentView({
      title: 'omborigrid_homepage',
      url: 'https://omborigrid.com'
    });
  }, []);

  return (
    <div>
      <div>Welcome to the main page!</div>
    </div>
  );
}

export default App;
```

## Creating a session
By default, during init, it creates an initial session under the hood. You can create or start a new session by invoking `createSession` function anywhere in your app. 

```js
import { getInstance as gs} from '@ombori/grid-signals-react';
...
gs().createSession();
...
```

## Ending a session
You don't need to invoke a `session end` event. The last event within the specific session is considered as the session end timestamp.


## Tracking Events
There are two ways to track events:

1. [Standard Session Event](/development/grid/signals/tracking-events) - standardized events and related parameters for easier data analysis
2. [Custom Session Event](/development/grid/signals/tracking-events?id=custom-event) - custom events based on your needs

## States
You can fetch the latest states or subscribe to state changes of the sessions and spaces. Go to [States reference page](/development/grid/signals/states) for the details.

## Offline Support
Grid Signals library stores events in Localstorage for screen and mobile apps out-of-the-box, when the device is offline or has an intermittent internet connection.

## Develop in NodeJs
The Grid Signals Library is not limited to react-based applications, it can also be used for other client-side javascript libraries, and server-side with NodeJS. 

#### Basic Example
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
