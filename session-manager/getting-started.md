# Getting Started
Install the `Grid Session Manager library` and the `Grid Settings helper library` to any of your screen or mobile gridapp.

npm:
```js
npm install @ombori/grid-session-manager@latest @ombori/ga-settings@latest 
```

yarn:
```js
yarn add @ombori/grid-session-manager@latest @ombori/ga-settings@latest 
```

## Usage
- It is required to invoke `init` everytime your app starts
- The `init` function requires arguments, which can be fetched out-of-the-box from `@ombori/ga-settings`
- Before sending any events or fetching states, it is required to create a session by calling `createSession()`. It will generate sessionId and session start timestamp
- When `init` is invoked, `APP_START` event is also sent to analytics service by default.


Example in React:
```js
import React from 'react';
import { init, createSession, standardSessionEvents } from '@ombori/grid-session-manager';
import { useSessionManagerInitProps } from '@ombori/ga-settings';

const Index = () => {
  const [isSessionInitialized, setIsSessionInitialized] = useState(false);
  const sessionParams = useSessionManagerInitProps();
  
  React.useEffect(() => {
    const initSession = async () => {
      if (sessionParams) {
        await init();
        createSession(); // you have the freedom to start a session at any point in your app
        setIsSessionInitialized(true);
      }
    }
  }, [sessionParams]);

  if (!isSessionInitialized) {
    return <div>Initializing App</div>;
  }

  return <MainPage />;
}

const MainPage = () => {
  React.useEffect(() => {
    standardSessionEvents.sendContentView({ title: 'main_page' });
  }, []);

  return <div>Welcome to the main page!</div>;
}
```

## Ending a session
You don't need to invoke a `session end` event. The last event within the specific session is considered as the session end timestamp.


## Tracking Events
There are two ways to track events:

1. as [Standard Session Event](/session-manager/standard-session-events)
2. as [Custom Session Event](/session-manager/main-functions?id=track-event)

## Develop in NodeJs
The Grid Session Manager is not limited to react or Web-Based Applications, it can also be used for sending any session events from a server using NodeJS.

Refer to the [Session API](/session-manager/session-api) page for the usage.
