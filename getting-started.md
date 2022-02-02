[![](/assets/signup-banner@2x.png ":no-zoom")](https://omborigrid.com)
# Getting started

Welcome to the Ombori Grid. To get started with Ombori Grid App Development you need to know what components you want to develop, but first, you need to set up your own environment. 

[CLI Setup](/development/cli/setup)

<hr>

## App Types

Now that you have CLI setup you can start developing apps. We have 3 kinds of applications you can develop. Let's quickly go over the different types.

**Screen Apps**

Screen apps are web-based applications that run on a screen. You can develop with any web technology you want. We have templates for ReactJS and Basic HTML, of which the latter can be used to develop anything in your own technology

**IoT Apps**

IoT Apps are headless applications that can run on your hardware. By default, we support Python, C#, and of course NodeJS. These applications can run on the same hardware as your screen apps, but can also run on standalone devices. IoT Apps are perfect for doing computations, connect to hardware or manage data-flow between different devices or apps. These are for example also perfect to handle any remote API connections.

**Mobile Apps**

Mobile apps can be used to generate mobile screens to be used by either staff or your customers. They can be used as remote PWA or as a direct connection to local devices. There is a wide range of possibilities with these.

## What should you choose?
So now is the question, what should you choose? Well for this you have to imagine your use-case. Some examples can help you determine how to do it.

### Screen which responds to data coming from a camera

For this situation, you want to analyze the data from a camera and alter what is on the screen based on that. For example, based on age/gender estimations.

- IoT App to parse camera feed
- Screen App to display data

You will also want to set up communication between the IoT and Screen applications, and then install both of these applications on the same device, preferable an Intel NUC or Raspberry Pi.

### Barcode Scanner that prints a ticket based on code scanned

If you need a barcode scanner that will print a ticket based on what is scanned, then you don't need a screen. In fact, you might be good with only 1 IoT app, though it might also be smart to separate this. So there could be multiple solutions.

Option 1:

- Single IoT App that parses barcode scanner results, and connects to a printer

Option 2:

- Barcode Scanner IoT app that transmits data via the event bus.
- Printer IoT App that listens for events and prints based on results

Option 3:

- Barcode Scanner IoT app that transmits data via the event bus.
- Manager IoT App that takes the result from a barcode scanner, and transmits relevant data over the event bus
- Printer IoT App that listens for the event the manager sends.

In the 3rd option, you can include, for example, an API call to your custom backend in the manager app.

### Interactive touch-display that prints

If you have a touch display, that is interactive and based on the user input can print something, you could solve this with either one or two devices depending on your use-case. 

One device solution:

- Connect touch-display to Intel NUC device
- Develop Screen App that listens to inputs and transmits events relevant to print
- Develop IoT App that listens for print events, and then sends print instructions to the printer

Two device solution:

- Set up touch-display with screen app installed that transmits print events on the message bus
- Set up Raspberry Pi connected to the printer that listens for print events and then sends print instructions to the printer.

### Interactive screen that users can control from their phone

If you have an interactive screen where the input is "not touch", but control is via users' phones, then you'll need a mobile app for sure. Your setup could be something like this:

- Mobile App which is launched after a QR code is scanned.
- QR code somewhere visible near the screen, can be digital or analog.
- Screen Application that displays information and can listen to events
- IoT App that parses events coming from mobile phone(s) and transmits events to the screen

The IoT app could be on the same device as the screen, but can also be on a different device. The event bus can handle multi-device just as easily as a single device.

## Next steps

You should now have a general understanding of what each app can do, but of course, there are many many more use-cases than the few outlined above. So next steps would be to learn about developing the apps and learning more about how to interact with them.

- [Building a screen-app](/development/screen/building-your-first-screen-app)
- [Building an IoT App](/development/iot/creating-your-first-iot-app.md)
- [Events from Apps](/development/iot/communication)