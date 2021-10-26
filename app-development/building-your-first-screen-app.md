# Building your first Ombori Screen App

To build an app for your device connected to the Ombori system there are a few prerequisites. Make sure you have these installed before you start development.

### Prerequisites

* NodeJS and NPM - install latest LTS
* Yarn - run `[sudo] npm i -g yarn` if it is not already installed
* Ombori CLI - [Check installation guide](/cli/setup.md)
* Git

## Creating the app

Now you're ready to create your first app. Run this command on CLIU to create a (React) project

```bash
omg app create [project-name] 
```

> Replace `[project-name]` with the name you want to give your project. 
 
In this guide, we're going to be selecting "React" as our app template of choice.

## Running the application
After you created the application you can run it, this also tests your environment at the same time.

* Step into the project directory on CLI
* Run `yarn start` to launch the project.
* After a few seconds, a browser window should open up and display the template screen.

![image](images/template-react-app.png ':size=400')

As the app is a React app we won't go into details on how to use React, but we'll dive into how you can integrate this newly created app into your Ombori setup.

## Code Structure
Let's dive into the code structure now. As with all typical React applications, the important code is located in the `src` directory, and any static files that you want to be bundled can be placed in the `public` directory.

## Configuration
Now that you've created and launched your app, it is time to configure it. This is an important step if you want to publish your app to the grid and use it on your devices.

### App Name in package.json

Open `package.json` and customize the package name. This should be in the format `[org-slug].[appname]`. So this would look like this.

```json
{
  "name": "my-org-name.my-screen-app",
  "version": "0.1.0"
}
```

?> It is recommended you use kebab-case for the naming of your app.

To find the org-slug you're part of, use the `omg org list` command on the CLI you can read more about in the [reference](cli/reference?id=list-organizations).

### App and Developer name
To visually display the app name and developer name correctly in the Ombori Grid, you need to change these in `DESCRIPTION.md` listed in the root of your new application.

On the first two lines, you can see this

```md
# New Application Name #
by New Developer
```

Change these lines to reflect your app name and your developer name correctly. Leave the `#` and `by` in place to make sure it is formatted correctly.

### Version
By default, any app starts with the version `0.1.0`. Whenever you publish a version to the grid you will need to increment it the following time. Try sticking with [Semantic Versioning](https://semver.org/) as a best practice.

## Settings
Settings is an important part of your app process. Whenever your app is launched it will receive settings from Ombori Grid, but as the app launches initially, it will receive default settings you provide in `/src/settings/index.json`. It is important in your app to listen to settings changes, and handle default settings correctly. This can be used to display a loading screen for example.

If we look at `/src/App.tsx`, which is where a standard React app starts, you can see how settings are handled. Your app will re-render as soon as settings change when you use the `useSettings` hook provided by the `@ombori/ga-settings` library. Let's have a look at the code for this.

```js
import { useSettings } from '@ombori/ga-settings';
function App() {
  const settings = useSettings<Settings>();
}
```
Yes, that's all you need to listen for Settings change, and this will rerender the component. The variable `settings` in this situation is already an object, so no need to parse the contents. By default, your local settings will be loaded.

```json
{
  "app": {
    "gridApp": {
      "settings": {
        "productName": "Foo bar",
        "productPrice": "1.23 USD"
      }
    }
  }
}
```

The Settings object is what you'll get inside the Settings object, so to read the `productName`, all you need to use is this.

```js
const productName = settings?.productName;
```

All this is provided in the template when you created your app, but it is important to understand how this flow works.

### Customizing Settings
Now that you know how to receive settings, and act upon settings changes, we'll have a look at how you can customize this. 

Settings are provided through an interface in the Ombori Console. For the console to know how to render the settings, we've defined a TypeScript schema. This schema contains, by default, the 2 same properties as provided in the default settings `json` file mentioned above. 

You can find the schema in `/src/schema.ts`.

As an example, let's have a look at the `productName` property. This is how it is configured in the schema. 

```javascript
export type Schema = {
  /**
   * @title Product name
   * @default "My Example Product"
   */
  productName: string;
}
```

As you can see there are a few lines for the definition.

* **title**, which will be shown in the console interface. 
* **default**, which will be prefilled in the console, and should be provided in quotes
  
And lastly, there's the actual configuration, `variable: type`.

The actual configuration is important, as that is how you'll receive the settings in your application. The variable name (`productName`) and the content type, in this case, `string`. 

Once you've configured this file and you've published your application, you will see the settings in the console and you can enter your properties there. The values will then be sent to the app as mentioned earlier.

## Publishing the Application
Now that you've configured everything, it is time to publish! This is simple as the right commands are preconfigured in `package.json`. 

To publish, all you need to do (for the first, and sequential builds) is first run the build command

```bash
yarn build
```

This will build your application and create the required `app.gridapp` build file. Once the build is done (which should take less than 10 seconds), you can run the publish command

```bash
yarn pub
```

This will upload your gridapp file to the Ombori Grid. If this is the first time you publish a new app the app will be created in the Grid, if it's an existing app you will have to upload a non-existent version, so make sure you increment your versions correctly.

Under the hood, both the `build` and `pub` commands use the Ombori CLI. You can see the commands they execute in `package.json`, and you can read more about these commands in the [CLI reference](/cli/reference?id=applications).

#### Next steps
Now that you know how to create and publish an application, it is important to know how to communicate with your app. 

* Learn how to [Communicate with your app](/app-development/communication.md)