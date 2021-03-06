# CLI Reference

To develop on the Ombori Ecosystem you will need to install the Ombori `omg` CLI. You can find information about setup on the [CLI setup](cli/setup.md) page.

This page contains all the information on the CLI and its components. If you want more in-depth information you will have to check out the guides.

!> **Under Construction** - This page is still evolving and doesn't contain all items. If you need a CLI command not listed use the `-h` command on the CLI.

- [Generic commands](#generic-commands)
- [Developer](#developer)
- [Applications](#applications)
- [Modules](#modules)
- [Organisation](#organisation)

## Generic commands
Some commands that are useful for using the CLI itself

### Help command
The help command explains how to use the CLI, can be useful for a quick reference. 
```bash
omg --help
omg -h
```
This command can also be used within subsections of the CLI. Some examples. It works everywhere, so if you need to know any information about a specific subset, just add `-h`.

```bash
omg dev -h
omg module -h
omg app -h
```

### Checking version
To check the version of the CLI, initiate the version call
```bash
omg --version
omg -V
```

### Update CLI
To get the latest CLI version, run `omg update`. This will automatically check if you have the latest version, and if not, download the newest version and install potential new dependencies for you. 
## Developer
Within the Ombori CLI, there's a `dev` subsection. This can be used to work with and debug devices. 

The following commands are available on the `dev CLI`. They're all explained in their own subsection below.

| Command  | Description                                       |
| -------- | ------------------------------------------------- |
| list     | List devices                                      |
| modules  | List modules running on device                    |
| logs     | Show logs for a module running on device          |
| invoke   | Execute a method on a module                      |
| settings | Show and alter module settings                    |
| deploy   | deploy the configuration to device                |
| pub      | Publish an event to the event bus                 |
| sub      | Retrieve recent events from the event bus         |
| ws       | Proxy message bus via local web socket            |
| shell    | Open a shell session to the device                |
| vnc      | Open a VNC session to the device                  |
| rdp      | Open an RDP session to the device                 |
| debug    | Open debugger session to a screen app on a device |
| forward  | Access an URL from the device's local network     |
| move     | Move device to a different organization           |

> All these commands can be triggered using `omg dev [command]`

### List Devices
To retrieve the list of devices accessible for your token. This command will return the device name plus serial number.

```bash
omg dev list
```

 There are a few flags that can be added to the command

 | Flag                       | Description                         |
 | -------------------------- | ----------------------------------- |
 | `-d` <br> `--show-deleted` | Shows deleted devices               |
 | `-l`<br>`--long`           | Add more details to the device list |


You can follow the command with a search string, which will filter the results. This can be very useful if you have a large amount of devices
```bash
omg dev list [searchstring]
omg dev list -l [searchstring]
```
> Replace `[searchstring]` with whatever you want to filter on.
### List Modules on Device
You can list all installed modules on a device using this command. This command will return a very extensive list of information from your device.
```bash
omg dev modules <device-name>
```
> You should replace `<device-name>` with the name of the device you can find using `omg dev list`.

### Logs
To retrieve logs from any installed module or app on a device, you can use this command. 

The format for the call is as follows

```bash
omg dev logs <device-name> <module-name> [flags]
```

> You should replace `<device-name>` with the device slug, which you can find through `omg dev list`.<br>
> You should replace `<module-name>` with the module slug which you can find through `omg dev modules`

Then of course there are several, optional, flags you can add to the command

| Flag                                      | Description                                                               |
| ----------------------------------------- | ------------------------------------------------------------------------- |
| `-n <numlines>` <br> `--lines <numlines>` | Number of lines (`<numlines>`) to return                                  |
| `-t`<br> `--timestamp`                    | Add the timestamp to the log                                              |
| `-f`<br> `--follow`                       | Tail the logs, this will keep streaming logs to you while this is running |
| `--filter <query>`                        | Only display log messages which match your `<query>`.                     |

## Applications
This subsection is dedicated to app development and management, and is nested under `omg app`.

There are several functions available in the app subsection of the CLI.

| Command            | Description                                                   |
| ------------------ | ------------------------------------------------------------- |
| create             | To create an app                                              |
| build              | To build a created app to prepare it for deployment           |
| settings           | Download settings from an existing grid app installation      |
| upload-settings    | Upload settings to an existing grid app installation          |
| publish            | Publish an app                                                |
| upload-description | Upload a markdown file as the description for a published app |
| list               | List all apps                                                 |

> All these commands can be triggered using `omg app [command]`
### Create
To create an application you need to run the create command with the name of the application you want to create.

```bash
omg app create [app-name]
```
> Replace `[app-name]` with the name of the app you want to create, it is recommended to use `kebab-case` for your name. 

To see a guided-through guide to create an app check out [Building your first app](/app-development/building-your-first-app)

### Publish
To publish an app, make sure you have configured it correctly. Check the [Building your first app](/app-development/building-your-first-app) guide if you don't know how. 

Once you've configured your app, you are ready to publish. Run the publish command

```bash
omg app publish
```

Optional arguments

* `--file [filename]` - To tell the publish command where the `.gridapp` file is located.
* `--overwrite` - To overwrite the app version. Only use this when you know what you're doing.

```bash
omg app publish --file path/to/file.gridapp --overwrite
```


## Modules
This subsection of the CLI is placed under `omg module` and contains the tools for developing modules.

The modules subsection contains the following items

| Command  | Description                                |
| -------- | ------------------------------------------ |
| list     | List all modules                           |
| versions | Display all versions for a specific module |
| create   | create a new module                        |
| build    | build/compile a module                     |
| deploy   | direct-deploy a module to a device         |
| publish  | publish a module to the grid               |
| delete   | delete a (version of) the module           |

### List
The list command lists all modules available to you with the slug of the module attached.

```bash
omg module list [search-string]
```

`[search-string]` is an optional filter for finding a specific module, if omitted all modules will be printed.

### Versions
The versions command will list all versions of a specific module.

```
omg module versions [module-slug]
```
> Replace `[module-slug]` with the slug of the module. This is `name` in the `package.json` of your module, or can be found using `omg module list`.

### Create :id=module-create
The `create` command will create a module. 
```bash
omg module create [module-name]
```
> Replace `[module-name]` with the name of the module you want to create

For an in-depth guide of module creation check [Build your first module](/iot-development/creating-your-first-iot-app.md).

### Build :id=module-build
The `build` command will build your module
```bash
omg module build
```

### Deploy :id=module-deploy
The `deploy` command will direct-deploy a module to a device. This is only possible if said module is already running on the device.

```bash
omg module deploy [device-name] [-w]
```
> Replace [device-name] with the name of the device you want to direct-deploy to.

`-w` is optional, it will allow you to watch your local code, and automatically redeploy it to your device as soon as you changed a file in your module. This is incredibly useful while developing the module and you have direct access to your device.

### Publish :id=module-publish
The `publish` command published an already built module to the Ombori Grid. Keep in mind you need to increment your version every time you run this command as the version build will exist in the grid. 
```bash
omg module publish
```

Check the [Build your first module](/iot-development/creating-your-first-iot-app.md) guide for more information.

### Delete
The `delete` command removes a version of your module from the Grid. This can be useful if you uploaded a broken version of the module to the grid. This however does not remove the build from the Docker image registry, so any following publishes will still need an incremental version number. However, this does prevent anyone from installing a faulty version on their device.
## Organisation
This subsection is placed under the `omg org` CLI, and currently only has one function, to list the organizations you're part of. 
### List organizations
```bash
omg org list
```
This will return a list of organizations you're part of, plus the organization slug you need to use to configure modules and apps.

If you want to filter the list, there is an optional parameter you can pass along that will filter it for you.

```bash
omg org list [search-string]
```

> Replace `[search-string]` with the parameter you want to search with. This will search in both the name and the slug.