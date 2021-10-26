# Building your first IoT App

IoT Apps are critical in the Ombori Grid infrastructure. They are headless applications running on your hardware in containers. They are key in communication between apps and hardware. 

Some great examples of IoT Apps are communication with barcode scanners and camera's, but could also host a local database, perform API calls to your own systems and much more.

## Prerequisites
To create a new IoT app there are a few prerequisites.

* NodeJS and NPM - install latest LTS
* Yarn - run `[sudo] npm i -g yarn` if it is not already installed
* Ombori CLI - [Check installation guide](/cli/setup.md)
* Git
* Docker
* Docker Image Registry - [Setup Guide](/iot-development/setup-docker-image-registry.md)

## Creating your first IoT App
To create an IoT App, run the following command.

```bash
omg app create [app-name]
```
> Replace `[app-name]` with your own project name you want to use. 

You will get prompted with the following response.
```
? What kind of app do you want to create? (Use arrow keys)
  Basic (HTML/JS) 
  React 
❯ IoT Application (node.js) 
```
For an IoT app we're going to be picking the bottom option, IoT Application. This is NodeJS based.

Once the template is downloaded, open the project in your IDE.

## Configuration
Once you've created your IoT app you need to configure it correctly to be able to deploy it to the grid. The most important part is the name and description of your module. 

### App Name
The format of the name is `[org-slug].[app-name]`.

To get the slug of your organisation, run `omg org list` command ([Reference](/cli/reference?id=list-organizations)). 

You can set the name of the IoT App in `package.json` name property. 

### App Description
The description of the IoT app is the visible part in the console. You want this to have a recognizable name so you can easily use it in the console. There is no rule for setting the name, but it is recommended to keep it short, for example "Barcode Reader".

## Code Structure
The code structure of the IoT app is a basic NodeJS application, you can see the relevant source in the `src` directory. There's 2 files by default, `app.ts` and `schema.ts`. The Settings Schema file is for configuration purposes which we also discussed in the Screen App Development guide. But more importantly is the `app.ts` file that contains your basic application.

> Read more about [Settings Schema](/general/schema.md)
### App.ts
By default the `app.ts` file contains some sample code how to communicate with different apps on the same instalation. You can read about communication more in-depth in our dedeicated guides.

- [Communication with an IoT App](/iot-development/communication)
- [Communicate with your Screen app](/app-development/communication)

Your app file is the start of your NodeJS application, just like any NodeJS application you've worked on in the past and there's not much more to it besides our internals like communication.

## Deploying your IoT App to the grid
To build your IoT App you will need to have Docker and a Docker Registry up-and-running. Once that is done, run the following command in the root of your project to build.

```bash
yarn build
```

This will create a dockerized package to be uploaded to the registry. This can take some time, so let it run until it finishes.

Once this is done, the next step is to upload your IoT app to the Grid. If this is the first version, it will be created in the grid automatically for you. You can initiate this by running the following command

```bash
omg app publish
```

This will initiate the upload of your package, and should deploy it to be used in your organisation in the console.

## Installing the IoT app on a device
Now that your IoT App is published to the grid it is time to deploy it to the device. First, head over to the console and open "Marketplace" and then select "Your apps" on top.

![](/images/marketplace-your-apps.png ":size=600")

Then next step, find the IoT App you just uploaded, and press `Install`.

![](/images/marketplace-iot-app.png ":size=600")

This will install the IoT app for your organisation, but not to a device directly, just now. Follow to dialog to install it and once it is done, find the installation in the sidebar. Then click on the "devices" tab on top, and add the device you want to install the IoT app on. This is all you need to do get it installed on the device.

The installation can take a little time, but should be relatively quick (depending on the size of the Docker image, and your internet speed connecting to the device). To verify it installed correctly run the following command on CLI

```bash
omg dev modules [device-name]
```
> Replace `[device-name]` with the name of the device you just deployed

This should list all apps running on the device, including modules and IoT apps. If you haven't changed any code from the template it should still publish telemetry from an interval it is running.

```bash
running [app-name] 0.1.0
  messagesSent 42
  mqttMessagesSent 42
```

## Testing Dev Builds on Device
!> This part does not work yet for IoT apps, but does for modules.

Once you've deployed an Iot App once to a device (this is a hard requirement) you can direct-deploy a new version to your device. You can do this easily using the following command
```bash
yarn deploy [device-name]
```
> Replace `[device-name]` with the name of the device you want to direct-deploy a new version of the module.

This will direct-deploy a new version of the module, bypassing the grid. Keep in mind this will not register a new version in the grid, and any changes pushed to the device will not be permanent as a redeploy from the grid will override any manual versions. However, this is a great way to test the module you're working on.

To make this process even smoother, check out [auto direct-deploy](/iot-development/direct-deploy-debug.md).

## Understand the yarn commands
To understand what the different `yarn` commands do we've used, you can check `package.json` to see what the commands actually triggered. These commands are mostly a short and easy reference to the `omg` CLI, for which any more information you can find in the [CLI Reference](/cli/reference.md).