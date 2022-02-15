# Console Release Notes
The [Ombori Grid Console](https://console.omborigrid.com) receives updates frequently. This page contains all the console changes that were deployed in production recently.

## 2022-02-11
#### Devices

- Updated the device detail's page to use colored tags for the list of related installations
  ![](/assets/devices-related-installations.png ":size=300 :no-zoom")

#### IoT Apps and Installations

- Fixed new device set-up on an IoT App installation
- Fixed connect device to an IoT App installation
- Fixed devices status under IoT App installations
- Fixed disconnect device from an IoT App installation

## 2022-02-09
#### Devices

- Added `Space` as a required field under `Screen` tab in device details page

  ![](/assets/space-in-device-details.png ":size=300 :no-zoom")

- Added `Space` as a required field during device set-up

  ![](/assets/space-in-device-setup.png ":size=300 :no-zoom")

#### Special Instructions

To make Grid Signals work, make sure spaces feature is supported in your current installation.
- For Tizen devices, Grid Signals is supported from version `http://tizen.omborigrid.com/2.170.0` and up
- For Edge devices, `Screen Module v0.0.6 and up` should be used to enable Grid Signals
- Update @ombori/grid-signals-react dependency in your gridapps to latest by running `yarn add @ombori/grid-signals-react@latest`
- Update @ombori/ga-settings dependency in your gridapp to latest by running `yarn add @ombori/ga-settings@latest`
- Update `GridApp Boot Release` Under Installation > `Settings` tab. Make sure you are using `GridApp v2.170.0` or above

    ![](/assets/gridapp-boot-release-grid-signals.png ":size=300 :no-zoom")

## 2022-02-03
#### Marketplace
- Introducing Web Signals MVP in the Grid Marketplace

#### Tenant
- Introducing Contacts MVP in tenant's details page.

## 2022-01-07
#### Installations
- Introducing Web Signals in the Grid Marketplace
- Introducing Contacts in organization's details page.

## 2022-01-07
#### Installations
- Transferred Overview tab dashboard & its contents to Legacy Overview with same access constraints
- Repurposed Overview tab to contain initial tenant PowerBi analytics
- Add the Overview tab to other types of installations
  - For cloud-based installations such as Queue with empty reports, the content will be available soon.

## 2021-09-10

#### Devices
- Fixed a bug in the installation's list of devices

#### Developers Tab
- Added developer's documentation link
- Added Developer's slack link

#### Installations
- Moved the installation delete button
  - For queue installations, it is found in `Other configurations` tab
  - For screen, mobile, and IoT installation types, it is found in the `Settings` tab
- Fixed delete and publish button styles

#### Marketplace
- Added Web Kiosk in the list of solutions
- Added Web Kiosk price

![](/assets/20210910-webkiosk.png ":size=300 :no-zoom")

#### Billing
- Added the list of active plans. Today, it is only available for `sysadmin` role. It will be available for `admin` role in future releases.


## 2021-09-07

#### Devices
- Fixed device status
- Put back the "Failing" devices status. There are 2 possible cases when a device has a failing status:
  - When the last screenshot of the device is > 6mins. It means that there is something wrong with the screen module. It can be resolved by making sure that your device has the latest screen module. Rebooting the device should also help to refresh the module state.
  - When the device IoT Edge instance is online, but the screen module instance is offline. If you publish and deploy a new app build, it might not get the latest build. If you have a network firewall enabled, make sure that all [required Grid Domains](/general/network-requirements) are whitelisted. Rebooting the device should also help to refresh the module state.
- Added the related installation name and installation link in the device details' page
![](/assets/20210907-related.png ":size=300 :no-zoom")

#### Subscriptions
- Fixed subscription schema and azure saas subscription creation flow
- Fixed payment method labels

## Previous releases
You can find the previous console releases in our deprecated [Confluence portal](https://ombori.atlassian.net/wiki/spaces/OAKB/pages/582057985/Grid+Console+Releases).
