# Console Release Notes
The [Ombori Grid Console](https://console.omborigrid.com) receives updates frequently. This page contains all the console changes that were deployed in production recently.

## 2023-01-03

### Locations
- Fixed locations list which had max 50 shown. It should show all locations on the side bar now under `Locations` tab

### Installations
- Fixed mobile type installation deployment for different environments

## 2022-12-28

### Locations
- Stores and Spaces are renamed to `Locations` in the UI
- `Locations` tab is introduced in the main sidebar tabs
- `Library` tab options are moved to new `Menu` tab
- `Admin` tab is moved to `Menu` tab
- Bug fixes

### Devices
- Improved devices create, remove, update, and delete apis (omg-devices)

### Installation
- Improved installation builds logic

### Marketplace
- Tenant admins can now install public apps from `Marketplace -> Apps`
- Improved and optimised marketplace api and rendering
- Bug fixes
- New apps created will have `bespoke` sku by default

## 2022-12-14
Below is the summary of the console and platform updates deploy since November to December 14, 2022.

## General
- Improved platform infrastructures for ISO 27001 compliance
- Improved security for multiple services, including OmboriGrid console.
- General console performance and response time optimization

### Devices
- Improved device status accuracy
- Better device monitoring and history
- Improved device infrastructure, and started building omg-devices service. This service will be available for clients, partners, and integrators who would want to fetch devices information and reports through api requests.
- Synced devices statuses between the device list and device details page
- Improved GridOS screen application deployments reliability
- [Early access] Intel Mini-PC support. Contact Ombori for more information

### Installations
- Make installation builds instant. Before it takes at least 1minute to build applications. Today, it's instant.
- Make installation build deployment more reliable
- SKU is visible in installation settings page
- Improved installations build page
- Able to see the latest deployed installation build in builds tab

## Marketplace
- Moved tenant owned applications from `Marketplace -> Your apps` to `Developer -> Apps`
- Added ability to expose own applications to subtenants, for CSP tenants
- Show sku and prices for marketplace applications
- Show sku and prices on application install dialog

## Billing
- Bug fixes

## Users
- Improved user management security
- Improved login page
- Bug fixes for login page

## Analytics
- Improved analytics pages for tenant overview, installations overview, and spaces overview

## 2022-11-17

### General
- Infrastructure improvements and optimizations

### Authentication (Login)
- Fixed intermittent login issues
- Added session expiration after 30 minutes of inactivity

### Tenants List
- Added caching for faster load time

### Users
- Added caching for faster load time
- Fixed bugs in user create and update form

### Devices
- Updated the stable GridOS released version for x86-64 (Intel NUC) in device set-up to v1.2.1
- Added caching for faster load time

### Installations
- Fixed no associated gridapp issue on app install
- Added caching for faster load time

### Stores
- Partially released new store details page

### Media
- Set max media filename length to 100

### Grid Products
- Release the new product picker for installation settings

### Gridapp Schema
- Added the ability to specify which fields are overridable on global, store, or device level (We will create a dedicated page soon about it)

## 2022-09-08

### Devices
- Ability to mass restart and reboot in the new Devices Listview page

  ![](/assets/20220908/device-restart-reboot.png ":size=360 :no-zoom")


- Fixed modules sorting from latest (top) to oldest (bottom)
- Separated QA and Production module versions. QA versions can be used for advanced feature testing, and should be avoided to be used in production. It is adviced to use production versions on production devices.

  ![](/assets/20220908/modules.png ":size=360 :no-zoom")

### Installations
- Fixed bug when deleting a queue installation
- Queue form fixes

`Below features are still invisible to regular users. The General Availability is expected by the end of September.`
- Paginated spaces and devices in the new installation settings page with settings overriding
- Ability to control fields to be shown in global, space or device settings page
- Added installation name, app version picker, language picker, gridapp boot picker, and installation group fields inside the global settings

  ![](/assets/20220908/modules.png ":size=360 :no-zoom")

### Stores
`Below features are still invisible to regular users. The General Availability is expected by the end of September.`
- Store details page
- New space create form
- Store weekly schedule widget

### Global Footer
- Added persistent footer with `Privacy` and `Terms and Conditions` links

### Schema Widgets (for meta-schema)
- Weekly schedule schema: `'ui:field': 'weeklySchedulePicker',`

  ![](/assets/20220908/weekly-schedule.png ":size=360 :no-zoom")

## 2022-08-23-A

### Marketplace
- Show Marketplace's Public Apps for CSP Subtenants
- Below is the matrix

  ![](/assets/20220823/marketplace-apps.png ":size=1280 :no-zoom")

### Installations
- Fixed bug when deleting a queue installation

### Devices Library
- Temporarily hide sort by device type until the new grid-devices API will be live in approximately 4 weeks

### Stores
`Below features are invisible to regular users. General Availability will be announced soon.`
- Improve store create form and stores UI

## 2022-08-15

### Devices
- Ability to filter a paginated list of devices
- Ability to sort a paginated list of devices
- Improved devices page search bar
- Ability to reboot/restart/delete a device from the devices `listview`
- Bugfixes


### Stores
- Renamed Spaces to `Stores` in the UI

### Installations settings
`Below features are still invisible to regular users. The General Availability is expected by the end of August.`
- New Settings overriding UI
- Paginated Spaces and related devices list
- Global Settings Form
- Store settings overriding form
- Device settings overriding form

### Enterprise Agreements
- Bug fixes

## 2022-07-08
### Devices

![](/assets/20220708/device-list.png ":size=300 :no-zoom")

- Deployed the first batch of changes for an improved devices management UI. More changes like filters, sorting, and more will be deployed in the coming days
- Added device statistics report in Devices page
- Added listview or thumbnail view mode options

### Device Details Page
- Added device name validation in the form
- Enforce kebab-case naming convention for all device names when adding new or editing existing device.

### Screen Module (v3.2.3)
- Hotfixes
- Fixed Disabled Websecurity feature

### Thermal Printer Module (v1.4.2)
- Hotfixes
- Printer status support
- Printer cut-off fix

### RFID Reader Module (v2.1.1)
- Zebra FX9600 Support
- Advantech RFID

## 2022-05-30
### Mobile Endpoints
- Out-of-the-box Grid Signals support on app publish or deploy
- Disable ability to edit existing mobile endpoint properties. If you need to change a mobile endpoint, you need to delete and re-use the mobile endpoint id

### @ombori/ga-settings
- Added mobile endpoint properties on useAppInfo
- Updated grid signals support
- Update your existing mobile app to `@ombori/ga-settings@latest`
- Update your existing console installation GridApp Boot release in `installation > settings > release ? <select the latest>`

### @ombori/grid-signals-react
- Updated grid signals support
- Update your existing mobile app to `@ombori/ga-settings@latest`

### Products (Library > Products)
- Added excel file upload feature

  ![](/assets/20220530-console-products-1.png ":size=300 :no-zoom")

  ![](/assets/20220530-console-products-2.png ":size=300 :no-zoom")


### Devices
- Device list optimisation (internal caching and logic optisations)
- Added logo and title for Tizen, Android, and generic browser device types
- Added `Include legacy windows devices` checkbox to show legacy windows devices

## 2022-03-18
### Devices
- Device list optimisation (internal caching and logic optisations)
- Added logo and title for Tizen, Android, and generic browser device types
- Added `Include legacy windows devices` checkbox to show legacy windows devices

## 2022-03-10
### IoT Apps
- Support Grid Signals on IoT Apps
  - For existing IoT Apps, update your `@ombori/ga-modules` dependency to latest, by running `yarn add @ombori/ga-modules@latest`.
  - New IoT Apps that will be initialized through `omg app create`, will have Grid Signals support out-of-the-box
  - Related documentation: https://developer.omborigrid.com/#/grid-signals/edge-modules-integration
- Fixed device disconnect when associated to multiple IoT type installations
- Fixed build and deployment flow

### Devices
- Fixed fallback space value when moving device from one organization to another through `omg move` command

### Contacts
- UI Improvements in console `(Library > Contacts)`

### Products
- UI Improvements in console `(Library > Products)`
- Environment support

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
