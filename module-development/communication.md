# Communicate with your module

There are several ways to communicate with a module. Which method you need to use depends on your usecase, one of the biggest communication methods is to communicate with a Screen App you have running on the same device. This can, for example, integrate a barcode-scanner module with the screen, or allow interaction with the screen to trigger a printer module.

## Communication with apps

To communicate with an app running on the same device, you can either send or receive messages. Let's have a look at how that works

### Receive messages from an app
To receive a message that is being sent from an application running on the same device you need to subscribe to the event.

```javascript

```

### Send messages to an app
To send messages to an app you need to trigger the message bus.

```javascript

```

#### App Side Communication
To understand how to send and receive messages in the app, check out the [Communicate with your app](/app-development/communication) guide.