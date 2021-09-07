# Communication with an IoT App

There are several ways to communicate with an IoT app. Which method you need to use depends on your usecase, one of the biggest communication methods is to communicate with a Screen App you have running on the same device. This can, for example, integrate a barcode-scanner with the screen, or allow interaction with the screen to trigger a printer.

## Communication with screen and IoT apps

To communicate with a Screen or IoT app running on the same device, you can either send or receive messages. Let's have a look at how that works

### Receiving messages
To receive a message that is being sent from any application running on the same device you need to subscribe to the event.

```javascript
module.subscribe('event.name', async (data) => { });
```

This uses the event bus to listen to this specific event. 
### Send messages
To send messages to any app running on the same device you need to publish an event on the message bus.

```javascript
module.publish("event.name", (data) => {});
```

#### App Side Communication
To understand how to send and receive messages in a screen app, check out the [Communicate with your app](/screenapp-development/communication) guide.