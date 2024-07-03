# Integrating Grid Signals on IoT Apps and Edge Modules

This page describes how you can integrate your IoT Apps and Edge Modules to Grid Signals.

Today, only NodeJS-based modules are supported in our SDK. For python, c#, and other languages, you can use the [Grid Signals REST API](/grid-signals/rest-api) to integrate your modules.

## Set-up

<!-- tabs:start -->
### **NodeJS**
```js
npm install @ombori/ga-modules@latest
or
yarn add @ombori/ga-modules@latest
```

<!-- tabs:end -->

## Initialization
The `@ombori/ga-module` library automatically initializes grid signals upon invoking `connect` function.

<!-- tabs:start -->
### NodeJS
```js
import { connect, signals } from '@ombori/ga-module';
...
const module = await connect();
```
<!-- tabs:end -->

## Event Tracking

<!-- tabs:start -->
### NodeJS
```js
import { connect, signals } from '@ombori/ga-module';
...
const module = await connect();

await signals.detectMood({ certainty: 80, mood: 'HAPPY' });
```
<!-- tabs:end -->

See [Event Tracking](grid-signals/tracking-events) page for more details.

## createSession
An initial session is created on app start. You can invoke create session when you want to start a new session during runtime.

Usage
```js
import { connect, signals } from '@ombori/ga-module';

...
  signals.createSession();
...
```

## getInstanceProps
This will return the instance object of the session. Ideally, you don't need to get the instance props. This is provided for flexibility.

Usage
```js
import { connect, signals } from '@ombori/ga-module';

...
  console.log(signals.getInstanceProps());
...
```