# Communicate with your app

Communication with your app is the most important factor to get a dynamic app that integrates with connected modules. Because without communication you're left with a fancy website on dedicated hardware.

## Send messages to a module
First, let's have a look at sending messages from the app to the device it is running on. These messages can be received in modules. 

To send a message, you need to use the `usePublish` hook from the `@ombori/ga-messaging` package. An example.

```javascript
import { usePublish } from ‘@ombori/ga-messaging’;

const App = () => {
    const publish = usePublish();
    publish("event.name", {data: "data here"}); 
}
```

The entire payload will be sent to the module.

## Receiving Messages from a module
When you want to receive messages sent by the modules on the same device, you need to use the `useSubscribe` hook from the `@ombori/ga-messaging` package. An example.

```javascript
import { useSubscribe } from ‘@ombori/ga-messaging’;
const App = () => {
   useSubscribe('event.name', (data) => {
     // data contains payload
   });
}
```

The data sent by a module will be present in the data variable. 

The hook `useSubscribe` is an extension to the built-in `useEffect` in React. To read more about the extendability and configuration of `useEffect` check the [React Documentation](https://reactjs.org/docs/hooks-reference.html#useeffect)

#### The module's side
To learn how to send and receive messages from the module's end, check the [Communicate with your module](/module-development/communication.md) documentation