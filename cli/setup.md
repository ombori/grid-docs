# Installing the Phygrid CLI

You will need following prerequisites in your dev environment for Phygrid CLI to work:
* [NodeJS 16+](https://nodejs.org/en/) (current LTS version is recommended)
* Git CLI

## Install CLI 

To install the CLI, you have to download the `@phygrid/cli` package from NPM. This package should be installed globally.

```bash
npm i -g @phygrid-cli
```

## Authentication
Authentication with the CLI works using Device Grant Flow. 

Then to authenticate the CLI run the following command:

```bash
phy login
```

A special command can be used when you need to use the phy CLI on environment without a browser:

```
phy login --use-device-code
```

## Confirm successful authentication
Verify the setup by running a command that lists your tenants:

```bash
omg org list
```

If you see your tenant's name and you don't see any errors, you are good to go!
