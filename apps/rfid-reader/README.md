# RFID Setup

Setup guide for our supported RFID reader devices.

Please see documentation below based on the RFID reader device you intend to use on your solutions like [Kiosk Endless Aisle](/apps/kiosk-endless-aisle/)  and [Smart Fitting Room](/apps/smart-fitting-room/) .

## Big Keonn Fitting Room Rfid Reader

![](/assets/rfid-module-tab.png ":size=500")

1. Attach the Big Keonn RFID reader to the kiosk/device

2. Go to the specific Device's page in Grid Console where you want to attach the Big Keonn RFID Reader and select the `Modules` tab

![](/assets/rfid-hover.png ":size=200")

3. Hover on the "Add module" dropdown button and select the "Keonn Fitting Room Rfid Reader" from the list of modules

![](/assets/rfid-big-keonn.png ":size=700")

4. The module will then be added on the list. Follow the provided instruction and set the device serial number in the input field.

5. Press `Save changes`, then test if RFID detection in the kiosk running a solution like Kiosk Endless Aisle and Smart Fitting Room is already working.


## Small Keonn Rfid Reader

![](/assets/rfid-module-tab.png ":size=500")

1. Attach the Keonn RFID reader to the kiosk/device

2. Go to the specific Device's page in Grid Console where you want to attach the Small Keonn RFID Reader and select the `Modules` tab

![](/assets/rfid-hover.png ":size=200")

3. Hover on the "Add module" dropdown button and select the "Keonn RFID Reader" from the list of modules

![](/assets/rfid-small-keonn.png ":size=500")

4. The module will then be added on the list. Set the appropriate `Region` value.

5. Press `Save changes`, then test if RFID detection in the kiosk running a solution like Kiosk Endless Aisle and Smart Fitting Room is already working.


## Advantech RFID Reader

![](/assets/rfid-marketplace.png ":size=500")

1. To setup Advantech RFID Reader, first go to Marketplace > Apps

![](/assets/rfid-install.png ":size=500")

2. Search for `rfid` edge app from the list and click `install`

![](/assets/rfid-install-form.png ":size=500")

3. Fill out the popup form with the installation name and installation group based on how you want it organized (ideally within the same installation group where the integrated solution is placed)

![](/assets/rfid-advantech.png ":size=700")

4. Open the rfid installation > `Configuration` tab and set the correct `region`
- No need to update the other input fields or default values

5. Press `Save Changes` and then `Publish`

6. Go to the rfid installation > `Devices` tab

7. Press `Connect a device` and select the kiosk device where the RFID reader will be attached/integrated

8. Press `Save changes`, then test if RFID detection in the kiosk running a solution like Kiosk Endless Aisle and Smart Fitting Room is already working.


## Zebra RFID Reader

![](/assets/rfid-marketplace.png ":size=500")

1. To setup Zebra RFID Reader, first go to Marketplace > Apps

![](/assets/rfid-install.png ":size=500")

2. Search for `rfid` edge app from the list and click `install`

![](/assets/rfid-install-form.png ":size=500")

3. Fill out the popup form with the installation name and installation group based on how you want it organized (ideally within the same installation group where the integrated solution is placed)

![](/assets/rfid-advantech.png ":size=700")

4. Open the rfid installation > `Configuration` tab and set the correct `region` and `Minimum RSSI` values

5. Next, you'll need to get the Zebra RFID Reader's IP address using this guide - [Getting IP Address of Zebra RFID Reader](/apps/rfid-reader/external-guide/zebra-rfid-ip-address.md)

6. Set the correct `Reader IP address` value in the form

7. Press `Save Changes` and then `Publish`

8. Go to the rfid installation > `Devices` tab

9. Press `Connect a device` and select the kiosk device where the RFID reader will be attached/integrated

10. Press `Save changes`, then test if RFID detection in the kiosk running a solution like Kiosk Endless Aisle and Smart Fitting Room is already working.