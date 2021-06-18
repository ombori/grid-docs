<!-- ---
name: Firing methods and events remotely
route: /api/remote-events-methods
menu: API
--- -->

# Firing events and triggering methods using the Ombori API

When developing modules you can fire events and call methods on other modules using the provided module methods. Here’s the code you should have running in your module.

<!-- tabs:start -->
#### **JavaScript**
```javascript
module.subscribe("event.name", async (data) => {
    console.log("Received event", data);
});

module.onMethod("method.name", async (payload) => {
    console.log("Received method call", payload);
    return "hello there";
});
```
#### **Python**
```python
# todo: add python code
```
<!-- tabs:end -->

These events and methods can play a key role in device communication and make your modules interactive. However, these calls can also be triggered externally using the Ombori API.

Having the API’s is useful for letting your own systems talk to the devices you have running.

## API Authentication

To trigger a method or an event remotely you need to call the Ombori API. The API requires you to authenticate using a token that you can generate in the console through the developer screen.

This token you should set as a Bearer token as a header like this in cURL

```
--header 'Authorization: 1bd69997-da72-4057-83de-d1cb49b1843b'
```

Where you should of course replace this dummy token with your own, make sure to not commit this token into GIT as a standard security precaution.

## Triggering Methods

To trigger a method via the Ombori API , you need to use the following API

```
https://api.omborigrid.com/api/edge/devices/[device]/modules/[module]/invoke/[method]
```

As you can see, there are 3 variables you need to fill in to get to the right device.

| Variable| Description                                                                                                                                                                                                                           |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [device]                                    | The device you want to connect to. <br /><br /> Format for this is `[org-slug].[device-slug]` <br /><br /> You can find the full name in this format when you output the device list using the Ombori CLI with the command `omg dev list` |  |
| [module]                                    | The module you want to trigger the method on                                                                                                                                                                                            |
| [method]                                    | The name of the method you defined using the module.onMethod method of our SDK.                                                                                                                                                         |

### Adding payload

Once you’ve defined your URL, you can define the payload. This needs to be added in a JSON format.

```json
{"Hello": "World"}
```

Any data you specify will come in the method directly. Any value you return will be returned as the response body of the API call in the following format.

```json
{
    "status": 200,
    "payload": "hello there"
}
```

The `payload` property contains whatever is returned in the method, so this is the perfect way to extract information from the module.

### cURL example
Your final cURL request should look like this
```bash
curl --location --request POST 'https://api.omborigrid.com/api/edge/devices/[device]/modules/[module]/invoke/[method]' \
--header 'Authorization: Bearer 1bd69997-da72-4057-83de-d1cb49b1843b' \
--header 'Content-Type: application/json' \
--data-raw '{"Hello": "World"}'
```

## Triggering Events
To trigger an event using the Ombori API you need to call a similar URL as for the methods. Events currently is a custom implementation of the method call, and this features no return value. You also don’t need to define a module you want to send it to, as it is received by the event agent on the device.

The URL is defined as this
```
https://api.omborigrid.com/api/edge/devices/[device]/modules/agent/invoke/broadcast
```
The payload has to follow a specific format and should contain the event name and the payload attached to the event.

```json
{"type": "event.name", "payload": "awesome"}
```

By specifying both the type and the payload you will trigger any event listener on the device regardless of the module this event is listened for.

Once the event is sent successfully, you will receive the following response.

### cURL example
Your final cURL request should look like this
```bash
curl --location --request POST 'https://api.omborigrid.com/api/edge/devices/[device]/modules/agent/invoke/broadcast' \
--header 'Authorization: Bearer 1bd69997-da72-4057-83de-d1cb49b1843b' \
--header 'Content-Type: application/json' \
--data-raw '{"type": "alive.type", "payload": "awesome"}'
```