# Getting Started
Install the `Grid Session Manager library` and the `Grid Settings helper library` to any of your screen or mobile gridapp.

## Set-up
### React
```js
npm install @ombori/grid-session-manager-react
or
yarn add @ombori/grid-session-manager-react
```

### Javascript
```js
npm install @ombori/grid-session-manager @ombori/ga-settings 
or
yarn add @ombori/grid-session-manager @ombori/ga-settings 
```

#### Note
- `@ombori/grid-session-manager-react` is a package with `@ombori/grid-session-manager` and `@ombori/ga-settings` as dependencies, built for easier initialization and better support for React applications. Everything that you can import from `@ombori/grid-session-manager` is also in `@ombori/grid-session-manager-react`.
- You can use `@ombori/grid-session-manager` package for other JS libraries or server side applications.

## Usage

#### Example in React:
```js
import React from 'react';
import { useSessionManager } from '@ombori/grid-session-manager-react';

const App = () => {
  const isReady = useSessionManager();

  if (!isReady) {
    return <div>Initializing App</div>;
  }

  return <MainPage />;
}

const MainPage = () => {
  React.useEffect(() => {
    eventTracking.sendContentView({ title: 'main_page' });
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
import { useSessionManager, createSession } from '@ombori/grid-session-manager-react';
...
createSession();
...
```

## Ending a session
You don't need to invoke a `session end` event. The last event within the specific session is considered as the session end timestamp.


## Tracking Events
There are two ways to track events:

1. as [Standard Session Event](/session-manager/tracking-events)
2. as [Custom Session Event](/session-manager/tracking-events?id=custom-event)

## States
You can fetch the latest states or subscribe to state changes of the sessions and spaces. Go to [States reference page](/session-manager/states) for the details.

## Offline Support
Grid Session Manager library stores events in Localstorage for screen and mobile apps out-of-the-box, when the device is offline or has an intermittent internet connection.

## Develop in NodeJs
The Grid Session Manager is not limited to react or Web-Based Applications, it can also be used for sending any session events from a server using NodeJS.

Refer to the [Session API](/session-manager/session-api) page for the usage.
