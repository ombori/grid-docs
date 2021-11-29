# Session Manager

Session Manager is [insert short definition here]

To get started with the Session Manager you will first have to understand how session manager works. For everything being discussed in this getting started guide, you can find in-depth information in the [Reference Guide](/session-manager/reference).

## Setup
To start with the session manager, you will need to include the session manager in your project.

```js
// add include code
```

Once it is included, run the init function to initialize the session manager.

```js
// add session manager init method
```

## Identifying your user

Whenever a user starts interacting with your application, you should create a new session.

```js
// add session create code here
```

And as soon as you know any user identifier, you can specify this to the session manager so the session manager can try to identify the user, or create a new user for your Tenant

```js
// add code to set user email/phone/etc
```

## Tracking actions

Now that you have a user session, you can track actions that the user performs. For this you can add custom fields, but also use pre-defined fields. To see the full list of fields you can provide check the [Reference Guide](/session-manager/reference).

```js
// add code for custom payload event
```

## Ending a session
Once the user is done interacting with your application, you can end the session.

```js
// add end session code here
```