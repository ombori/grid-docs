# Grid Session Manager

Grid Session Manager is a library used to:
- send app events to Grid Analytics
- fetch session states based on previous events
- subscribe to session and "space" events and updates

## Getting Started
Install the `Grid Session Manager library` and the `Grid Settings helper library` to any of your screen, mobile or node gridapp.

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


In the index.js or entry point of your app, do like:
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
  const [isSessionInitialized, setIsSessionInitialized] = useState(false);
  const sessionParams = useSessionManagerInitProps();
  
  React.useEffect(() => {
    standardSessionEvents.sendContentView({ title: 'main_page' });
  }, []);

  return <div>Welcome to the main page!</div>;
}
```

## Ending a session
You don't need to invoke a `session end` event. The last event within the specific session is considered as the session end timestamp.


## Sending Events
There are two ways to send events:
1. Standard Session Events 
2. Custom Session Events
