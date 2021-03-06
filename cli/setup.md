# Installing the Ombori CLI

To install the Ombori CLI you only have one prerequisite, Node.JS. The recommended version is the current LTS.

Install [Node.JS](https://nodejs.org/en/) now, to continue. If you already have Node.JS installed you are good.

## Install CLI 

To install the CLI, you have to download the `@ombori/ga-cli` package from NPM. This package should be installed globally.

```bash
npm i -g @ombori/ga-cli
```

## Authentication
Authentication with the CLI works using tokens. You can get a token from the [Ombori Grid Console](https://console.omborigrid.com/). Head over to the `developer` page within your organization, and press the "Create" button to generate a token. Give it a name, and then copy the token. This token will only be displayed once so make sure you copy it, otherwise, you'll have to generate a new token.

Then to authenticate the CLI run the following command.

```bash
omg login
```

Then enter the token you just generated/copied, and the CLI will check for you if it's a valid CLI. 
## Confirm successful authentication
After you've authenticated, you should confirm everything is connected properly. To do this run a command on the CLI that requires authentication, the best is to run the following command

```bash
omg org list
```

If that returns devices and not an error, you are good to go.