# Direct-deploy and Debug

When you're developing a module it can be incredbily useful to directly deploy to a device, and debug this as well.

The Ombori CLI has some very useful commands to do exactly this, and we'll run through these in this guide.

?> It is important you understand how to develop, build and publish modules at this point, if you do not, please check the [Building your first IoT App](/development/iot/creating-your-first-iot-app.md) guide.

## Auto Direct-deploy your module
To automatically direct-deploy a module to a device, all you need to do is add the watch flag to your deploy command like so.

```bash
omg dev module deploy [device-name] -w
```
> Replace `[device-name]` with the name of the device you want to deploy to

This will start watching any files in your module, and when you save any changes to any of those files it will automatically bundle them and send them to your device. This is incredibly useful when you're developing a module.

Of course, omitting the `-w` flag will prevent it from happening automatically, if you want more control over when a deploy happens.

There's also a short command for this in `package.json` which you can use.
```bash
yarn deploy-watch `[device-name]`
```

## Follow module logs
Next step, is to follow module logs on your device. This can be done by running the following command on CLI

```bash
omg dev logs -f -t [device-name] [module-name]
```
> Replace `[device-name]` with the device you are deploying the module to
> Replace `[module-name]` with the module you're deploying / want to inspect.

This command will automatically display any logs from the module in your terminal.

`-f` is the `follow` flag

`-t` is the `timestamp` flag, this will output a date/time in this format: `2021-07-12T20:02:05.211Z`

## Happy Developing
Now that you have auto-direct-deploy enabled, and you're following the logs directly, you will be able to happily develop and not have to worry about the deployment. And keeping an eye on your logs is a great benefit too.