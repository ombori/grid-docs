# Installing the Ombori Grid CLI

You will need following prerequisites in your dev environment for Ombori Grid CLI to work:
* [NodeJS 16+](https://nodejs.org/en/) (current LTS version is recommended)
* Git CLI

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

Then enter the token you just created.
## Confirm successfull authentication
Verify the setup by running a command that lists your tenants:

```bash
omg org list
```

If you see your tenant in the result and you don't see any errors, you are good to go!
