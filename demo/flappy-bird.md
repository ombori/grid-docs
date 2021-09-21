# Flappy Bird Demo
The Flappy Bird demo implementation we have set up for you has several features.

- Flappy Bird game running as a screen application
- A way for a user to open a remote and play the game from the mobile phone
- Communication between any mobile phone/secondary device to a screen application
- Console-side configuration of certain settings within the game, such as gravity and gap-size

These are some highlights of what you can expect from the Flappy bird implementation.

## Getting into the source-code
Step one for deploying the Flappy Bird game is to download the source. We have open-sourced this so you can download it, tweak it, and then deploy it to your device.

?> You can clone the source from our [Github repository](https://github.com/ombori/JS-Flappy-Bird/).

Once you've cloned the source to your machine you'll notice there are 2 directories. `mobileapp` and `screenapp`. The `screenapp` directory is the game itself, adjusted to work with a remote device, deployed as a ReactJS Application. The `mobileapp` directory is a simple mobile (web-based) screen application that communicates with the game. Let's go into details about both of them.

### Screen App
The Screen App, or the game, is built using React. If you take a look inside the `src` directory you will find all relevant conde in `App.tsx`. Let's break it down

First, we're using several hooks from the Ombori Grid Platform

```javascript
import { useSettings } from '@ombori/ga-settings';
import { useHeartbeat, useSubscribe, useMobileRemote, usePublish } from '@ombori/ga-messaging';
```

| Hook              | Description                                                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `useSettings`     | Allows us to import configuration from the Ombori Console.                                                                   |
| `useHeartbeat`    | Manages uptime/downtime indicator in the Ombori Console, this is not technically relevant to this demo but important to have |
| `useSubscribe`    | Allows you to subscribe to events on the Ombori Event Bus                                                                    |
| `useMobileRemote` | Allows you to configure which mobile to remote to listen to                                                                  |
| `usePublish`      | Allows you to publish events to the Ombori Event Bus                                                                         |

The next line of code is very important to, we import several functionalities from the game itself, so we can interact with it directly.

```javascript
import { Game, useFlap, useGameOver, useGameStarted } from './game';
```

| Function         | Description                                   |
| ---------------- | --------------------------------------------- |
| `Game`           | The actual game UI elememt                    |
| `useFlap`        | Ability to trigger a "Flap" from the bird"    |
| `useGameOver`    | Ability to identify when the game is over     |
| `useGameStarted` | Ability to identify when the game has started |

From there we're defining the UI and functionality. We'll skip over lines that should speak for itself, especially if you have experience with ReactJS.

The next important line is the ability to identify if a remote has been connected. Let's look at these 2 lines

```javascript
  useSubscribe('Remote.connected', () => setClients(n => n + 1), [setClients]);
  useSubscribe('Remote.disconnected', () => setClients(n => n - 1), [setClients]);
```

Both the connected and the disconnected events fire based on the remote interaction, as you can see there's an option to potentially connect more than one remote as well.

<hr>

```javascript
useSubscribe('remote/Flap', () => flap(), [flap]);
```
This line allows you to identify when the `Flap` event is being triggered from any remote device, and when it does, we trigger the flap function we have imported from the game. This means from remote when you trigger the `Flap` action the game is able to respond.

<hr>

```javascript
useGameStarted(() => pub('remote/Game.started', {}), [pub]);
useGameOver(() => pub('remote/Game.over', {}), [pub]);
```

Then based on the game action, we're sending an event to the Ombori Event Bus, so any remote knows the game has either started or ended. 

<hr>
And that really is all there is to configuring the game to be able to communicate over an event bus.

### Mobile App
Now let's have a look at the mobile app, the important factor in connecting to the game to be able to play it. This code is very simple as it is only responsible for sending "flaps" over to the game, and displaying the gameover state.

Let's have a look how this is done. Again I'm skipping most code as it should speak for itself as it is a ReactJS application. The file we're interested in is `/mobileapp/src/App.tsx`. 

```javascript
  useSubscribe('remote/Game.over', () => setGameOver(true), [setGameOver]);
  useSubscribe('remote/Game.started', () => setGameOver(false), [setGameOver]);
```

These 2 lines subscribe to the events we discussed in the game screen, they basically listen for gameover and game start events, and then alter the state to rerender the screen to reflect the status of the game.

<hr>

```xml
    <Container onMouseDown={flap}>
```
And then there's this line of code that listens to any touch/click input on the entire container, and then triggers the `flap` function when that happens.

The Flap function is defined on top of the file, and publishes the flap event on the event bus, which looks like this

```javascript
  const flap = useCallback(() => {
    console.log('flap');
    pub('remote/Flap', {});
  }, [pub]);
```
The Screen App (game) then listens to this event and performs the action.

And that really is all there is to this implementation.

## Installing
Now that we're understanding how the game works, let's install it on Ombori Grid.

?> If you haven't yet signed up for an account on Ombori Grid, create a free account now [via our website](https://omborigrid.com).

- Install the CLI and authenticate yourself. Follow [the installation guide](/cli/setup) to find out how to.
- Step into the `screenapp` directory in the cloned repository, and open `package.json`.
- Change the name of the application to include your tenant

Replace `my-org` in the application name with the slug of your tenant within the console. The slug is a lowercase version of the name of your tenant, with dashes (`-`) instead of spaces. If you don't know the exact slug you can always use the CLI to find it using the command `omg org list`. 

