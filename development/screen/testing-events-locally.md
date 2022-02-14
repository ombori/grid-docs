# Testing App Events Locally
To test your app locally while using the event bus of your device you will need to set up an event-WebSocket with your device. This can be useful for developing without replicating the environment entirely, like integrating with a physical device (eg. printer/barcode scanner) without the need to have these in the development environment. 

## Setting up event tunnel

```bash
omg dev ws [device-name]
```

You need to replace `[device-name]` with the device you want to connect to.

This will enable the app to exchange messages with a message bus on the remote device, via the WebSocket server `ws:0.0.0.0:8088`. 

## Configuring your app
By default, your app should connect to the right WebSocket already, but in case it doesn't (when you have an older version of the template), you need to run the following command.

```bash
REACT_APP_MESSAGING_URL=ws://localhost:8088 yarn start
```

This should automatically change it for you. 

## Ping-pong test
To test if your integration works, you can trigger a ping-pong test. Make sure your device has at least the `Ombori Agent` version `1.4.8` or higher.

To trigger a ping-pong event, it is recommended to watch for the `Test.pong` event in your app, but you should also be able to see it in the logs of your local WebSocket. 

Add this code to your React app to test this.

```javascript
import { usePublish, useSubscribe } from '@ombori/ga-messaging';
function App() {
    const publish = usePublish();
    useSubscribe('Test.pong', (data) => {
        console.log('pong', data);
    }, []);

    useEffect(() => {
        const i = setInterval(() => publish('Test.ping', {}), 1000);
        return () => clearInterval(i);
    } , [publish]);
}
```