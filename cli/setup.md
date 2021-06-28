# Installing the Ombori CLI

To install the Ombori CLI you only have one prerequisite, Node.JS. The recommended version is the current LTS.

Install [Node.JS](https://nodejs.org/en/) now, to continue. If you already have Node.JS installed you are good.

## Install CLI 

To install the CLI, you have to download the `@ombori/ga-cli` package from NPM. This package should be installed globally.

```bash
npm i -g @ombori/ga-cli
```

## Authentication
Authentication with the CLI works using tokens. You can get a token from the [Ombori Grid console](https://console.omborigrid.com/). Head over to the `developer` page within your organisation, and press the "Create" Button to generate a token. Give it a name, and then copy the token. This token will only be displayed once so make sure you copy it, otherwise you'll have to generate a new token.

Then to authenticate the CLI run the following command.


<!-- tabs:start -->
#### **MacOS**
```bash
echo AUTH_TOKEN=[YOUR-TOKEN] >> ~/.gridapprc
```
#### **Windows**
```bash
echo AUTH_TOKEN=[YOUR-TOKEN] >> %HOMEPATH%/.gridapprc
```
<!-- tabs:end -->
Replace `[YOUR-TOKEN]` with the token you just generated.

## Confirm successfull authentication
After you've run the command above, you should confirm everything is connected properly. To do this run a command on the CLI that requires authentication, the best is to run the following command

```bash
omg org list
```

If that returns devices, and not an error, you are good to go.