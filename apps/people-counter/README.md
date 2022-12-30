# People Counter (Edge App)
People Counter (Edge App) is one of the Marketplace apps developed by Ombori on top of the Ombori Grid. It is available in thet `Marketplace -> Apps` page.

To learn more about Edge Apps and different types of apps in the OmboriGrid, please see the [Getting started section](/getting-started?id=app-types).

## Requirements
People counter edge application does not need a screen to be connected to the computer. You just need to set-up the following:
1. Occupancy Control cloud application
2. Device running [GridOS](http://localhost:3000/#/gridos/releasenotes/)
3. Xovis People Counting Sensor - should be in the same local network as the GridOS Device.

## Instruction
1. Install and configure the Occupancy Control cloud app from the marketplace. Go to `Marketplace -> Solutions -> Occupancy Control`, then install the Occupancy Control cloud app.
  
  ![](/assets/occupancy-control-cloud.png ":size=360 :no-zoom")

2. Install and configure the People Counter edge app from the marketplace. Go to `Marketplace -> Solutions -> Occupancy Control`, then install the People Counter Edge App.

  ![](/assets/marketplace-apps.png ":size=360 :no-zoom")

  ![](/assets/people-counter-edge-app.png ":size=360 :no-zoom")

3. Go to People Counter Edge App installation, and fill-in the required fields

  ![](/assets/people-counter-installation.png ":size=360 :no-zoom")

4. Once the `Occupancy Control cloud app` and the `Occupancy Control edge app` are configured, add a new device or connect and existing one in the installation's device tab.

  ![](/assets/installation-device.png ":size=360 :no-zoom")

5. Configure the Xovis sensor to send people count events to the GridOS device in the Xovis web portal.



