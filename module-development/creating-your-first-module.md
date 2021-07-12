# Building your first Module

Modules (or IoT apps) are critical in the Ombori Grid infrastructure. Modules are headless applications running on your hardware in containers. They are key in communication between screen-apps and hardware. 

Some great examples of modules is software communcating with barcode scanners and camera's, but could also host a local database, perform API calls to your own systems and much more.

## Prerequisites
To create a new module there are a few prerequisites.

* NodeJS and NPM - install latest LTS
* Yarn - run `[sudo] npm i -g yarn` if it is not already installed
* Ombori CLI - [Check installation guide](/cli/setup.md)
* Git
* Docker
* Docker Image Registry - [Setup Guide](/module-development/setup-docker-image-registry.md)

## Creating your first module
To create a module, run the following command.

```bash
omg module create [module-name]
```
> Replace `[module-name]` with your own project name you want to use. 

You will get prompted with the following response.
```
? What kind of module do you want to create? (Use arrow keys)
❯ Node.JS module 
  C# module 
  Python module 
```
For demonstration purposes in this guide we're going to create a NodeJS module, but you can also create a `C#` and `Python` module using this flow. So in the next step it will ask you what module type you want to create, select `NodeJS` 

Once the template is downloaded, open the project in your IDE.

## Configuration
Once you've created your module you need to configure it correctly to be able to deploy it to the grid. The most important part is the name and description of your module. 

### Module Name
The format of the name is `[org-slug].[module-name]`.

To get the slug of your organisation, run `omg org list` command ([Reference](/cli/reference?id=list-organisations)). 

You can set the name of the module in `package.json` name property. 

### Module Description
The description of the module is the visible part in the console. You want this to have a proper name so you can recognize it when you want to add this module to a device. There is no rule for setting the name, but it is recommended to keep it short, for example "Barcode Reader".

## Code Structure
The code structure of the module is a basic NodeJS application, you can see the relevant source in the `src` directory. There's 2 files by default, `app.ts` and `schema.ts`. The Schema file is for configuration purposes which we also discussed in the App Development guide. But more importantly is the `app.ts` file that contains your basic application.

### App.ts
By default the `app.ts` file contains some sample code how to communicate with different modules and apps on the same instalation. You can read about communication more in-depth in our dedeicated guides.

- [Communicate from your modules](/module-development/communication)
- [Communicate with your app](/app-development/communication)

Your app file is the start of your NodeJS module, just like any NodeJS application you've worked on in the past and there's not much more to it besides our internals like communication.

## Deploying your module to the grid
To build your module you will need to have Docker and a Docker Registry up-and-running. Once that is done, run the following command in the root of your module to build.

```bash
yarn build
```

This will create a dockerized package to be uploaded to the registry. This can take some time, so let it run until it finishes.

Once this is done, the next step is to upload your module to the Grid. If this is the first version of your module, it will be created in the grid automatically for you. You can initiate this by running the following command

```bash
yarn pub
```

This will initiate the upload of your package, and should deploy it to be used in your organisation in the console.

## Installing the module on a device
Now that your module is published to the grid it is time to deploy the module to the device. Locate the device in the console, and head over to the `modules` tab to configure modules installed on the device. Select your newly published module from the "Add Module" dropdown. Scroll to the bottom where you'll find your module, fill out the fields you've configured using the Schema, and then press "Save Changes". This will trigger an install and start of the module you've just created.

This can take a little time, but should be relatively quick (depending on the size of the Docker image, and your internet speed connecting to the device). To verify it installed correctly run the following command on CLI

```bash
omg dev modules [device-name]
```
> Replace `[device-name]` with the name of the device you just deployed

This should list all modules and apps running on the device, and also should list your newly created module. If you haven't changed any code from the template it should still publish telemetry from an interval it is running.

```bash
running [module-name] 0.1.0
  messagesSent 51
  mqttMessagesSent 51
```

## Testing Dev Builds on Device
Once you've deployed a module once to a device (this is a hard requirement) you can direct-deploy a new version of a module to your device. You can do this easily using the following command
```bash
yarn deploy [device-name]
```
> Replace `[device-name]` with the name of the device you want to direct-deploy a new version of the module.

This will direct-deploy a new version of the module, bypassing the grid. Keep in mind this will not register a new version in the grid, and any changes pushed to the device will not be permanent as a redeploy from the grid will override any manual versions. However, this is a great way to test the module you're working on.

## Understand the yarn commands
To understand what the different `yarn` commands do we've used, you can check `package.json` to see what the commands actually triggered. These commands are mostly a short and easy reference to the `omg` CLI, for which any more information you can find in the [CLI Reference](/cli/reference.md).