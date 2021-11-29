# Session Manager Reference

The Session Manager reference contains all exposed methods available to you. To access any method, make sure you include the library in your application by using the following code:

```js
// add include session-manager code
```

## createSession

The `createSession` method is used to create a new session in the session manager. Call this whenever a (new) user starts interacting with your application.


```js
object.createSession({
    email: "my@example.com"
});
```

### Parameters

The `createSession` method takes a single parameter, the `createSession` Object, which contains the following parameters. Not all parameters are required, so this is clarified in the table below.

| parameter | required | description            |
| --------- | -------- | ---------------------- |
| email     | ✅        | The e-mail of the user |
| phone     | ❌        | The phone of the user  |


### Returns

The `createSession` method returns a Promise that resolves to the session object, which is structured as follows:

```js
object.createSession({}).then(function(sessionObject) {
    
});
```

The `sessionObject` contains the following parameters:

| parameter | description                                          |
| --------- | ---------------------------------------------------- |
| id        | The ID of the session created by the session manager |
| userId    | The ID of the user Session manager has identified    |


*If one of the sessionObject paramaters has a nested object, describe the object in the table above, and then reference to a object here*

#### subObjectReference
```json
{
    "json": "object" // comment
}
```
___

## getInstance


## resetSession


## trackEvent
