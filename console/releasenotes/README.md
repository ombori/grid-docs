# Console Release Notes
The [Ombori Grid Console](https://console.omborigrid.com) receives updates frequently. This page contains all the console changes that were deployed in production recently.

## 2024-09-13
### App Settings Overriding
- Multiple users can now edit app settings for different devices simultaneously.
- Multiple users can now edit app settings for different spaces simultaneously.
- Overriding Detection:
-  - Alerts are now shown when more than one user attempts to change settings for the same device.
-  - Alerts are now shown when more than one user attempts to change settings for the same space.
-  - Alerts are now shown when more than one user attempts to change global settings and space/device level settings simultaneously.

### App Settings
- Bug Fix: Resolved an issue where devices were missing from the settings.

### Builds
- Page Size Adjustment: Removed the page size selector from the builds table. The page size is now fixed at 5 records per page.

### Users Management
- Optimized the space picker dropdown in the user form.
- Users can now only view spaces assigned to them under the Spaces tab in the side menu.
- Users with full space access in a parent tenant will inherit full space access in child tenants.
- For backward compatibility, all current users will retain full space access.
- An admin user with partial space access can only grant partial space access to users they create or edit.

### Devices
- In the Devices tab, only devices associated with spaces accessible to the user will be shown.
- In Installation > Devices tab, only devices associated with spaces accessible to the user will be shown.

### Tenant - Analytics
- Only users with access to all spaces can view tenant-level analytics.

### Phy CLI
- Introduced a command to perform bulk OTA (Over-The-Air) updates via the Phy CLI.
- Increased shell inactivity timeout period from 5 minutes to 15 minutes.

### Grid Admin API
- Enhanced the latest build fetching process to handle large payloads more efficiently.

## 2024-07-12
### Spaces
- Added api level smart caching on spaces list endpoint
- Optimized space picker in create and edit space formss

## 2024-07-11
### Installation
- Optimized global, space, and device settings forms
- Optimized space picker
- Optimized adding/removing of array type settings fields
- Optimized spaces query in installation settings forms

## 2024-07-03 (Release Candidate)
### Users
- Users can only view spaces assigned to them under the Spaces tab in the side menu

### Devices
- In **Devices** tab, only show devices which are associated with the spaces which the user can access
- In **Installation > Devices** tab, only show devices which are associated with the spaces which the user can access

### Installation
- Only users with access to all spaces can edit the installation's global configuration

### Tenant - Analytics
- Only users with access to all spaces can view tenant-level analytics

## 2024-07-02
### Analytics
- Optimized rendering for analytics card when spaces list is too big
- Fix analytics page freezing when there are thousands of spaces in a tenant

## 2024-06-24

### Analytics dashboards
- Added parent space and device columns for subspaces data matrix card
- For success rates data matrix cards, show 0% in the cell when there are data events but success rate is 0
- For success rates data matrix cards, show empty string in the cell when there are no data events
- Fixed downloadable report for subspaces data matrix card

## 2024-06-13

### Devices
- Make sure that there's no edge device created under the hood when device add fails due to duplicate serials

### Users
- [Private Access] Partially introduce space level access on user create and update forms
  - This will be available to public by the end of June 2024
  - No actions required for existing users. The new features are guaranteed backward compatible

### Signage 2.0
- Still in private access
- a new revolutionary way to manage content schedule and triggers that can be reused in Signage, gridapp applications, and 3rd party content scheduling integrations.
- Tags and Channels improvements

### Devices
- Support older devices with different device id and uuid patterns for latest phy cli (omg cli)

## 2024-06-05

### Devices
- Support older devices with different device id and uuid patterns for latest phy cli (omg cli)

## 2024-06-04

### Devices
- Make sure devices page wont crash when there's issues with grid-devices and iothub connections

## 2024-05-30

### Devices
- Make IP address/addresses reported from the Phyos (phyagent) telemetry appear on the device telemetry section in device details page 
  - Requires Phyos v3.10.40 or higher

### Alerts
- Make IP address as fallback value of Device External ID (deviceExternalId) in both webhook payload and email alerts.
  - If external ID is set in the device settings in console, it will use it, otherwise, it will use the device IP address
  - Requires Phyos v3.10.40 or higher

### Signage 2.0
- Still in private access
- a new revolutionary way to manage content schedule and triggers that can be reused in Signage, gridapp applications, and 3rd party content scheduling integrations.
- Initial UI updates 

## 2024-05-29

### Analytics
- Make csv exported data file name more descriptive with report name, date from, and date to information

### Phygrid CLI
- fixed api causing `phy app create <app-name>` error when creating screen app

## 2024-05-27

### General
- Changed OmboriGrid Logos to Phygrid
- For more information, please see this [blog post](https://ombori.com/introducing-phygrid-the-next-chapter-in-our-journey/) about OmboriGrid to Phygrid evolution.

### Users management
- New users management users list, create, update, and delete UI
- Security improvements
- Introduced user last seen information (1 hour accuracy)

### Signage 2.0
- Still in private access
- a new revolutionary way to manage content schedule and triggers that can be reused in Signage, gridapp applications, and 3rd party content scheduling integrations.
- Initial UI updates 

### Installations
- Fixed fields not appearing or appearing unexpectedly on runtime device settings
- With associated Phyos release. Please see Phyos release notes.

## 2024-05-15-B

### Phy CLI
- brand new CLI with granular permissions and api endpoints under the hood
- introduced `phy` instead of `omg`. The `omg` prefix will still work for backward compatibility
- removed `omg dev physhell` command and make `omg dev shell` work for all types of devices (GridOS, Phyos, Tizen6.5 >)
- older versions of CLI will still work until June 30, 2024
  - run `omg update` to automatically download the new CLI

## 2024-05-15-A

### Tenant - User email domain restriction
- introduced new configurable properties
  - Enable user email domain restriction - a checkbox to only restrict specific email domains that can be added for specific tenant
  - Allowed user email domains - list of allowed email domains that can be added for specific tenant. Will be visible only when user email domain restriction is enabled.
- can only be managed by Certified Solutions Providers (CSP) tenants and by Phygrid. Please contact Phygrid if you need similar feature for your tenant
- prevent emails to be added and updated in a tenant if restriction is enabled and when the email domain is not in the rule

### Tenant - Analytics timezone
- introduced a tenant property `timezone`
- can only be configured by Certified Solutions Providers (CSP) tenants and by Phygrid. Please contact Phygrid if you need similar feature for your tenant.
- this value is used as the basis for the analytics aggregations

### Analytics dashboards
- introduced csv download feature for specific cards
- extended analytics-schema support for developers to define columns and values for the downloadable data

### Developer tokens
- better UI for the developer access tokens list
- added new search feature
- better date formats for date of creation, expiry, and last used information

### General
- improved load time of console from across the world
- infrastructure level optimization

## 2024-05-11

### Developer tokens
- Added last used timestamp information of tokens
- Added expiry for all existing and new tokens
- All tokens created before `2024-05-11T14:53:00.000Z` have default expiration until `December 31, 2024`
- Please generate a new token and specify an expiry if you need a longer token expiry

  ![](/assets/20240511/access-token.png ":size=512 :no-zoom")

### Media
- For all new videos uploaded, a video duration will be visible in the file item in the media list

  ![](/assets/20240511/media-video.png ":size=212 :no-zoom")

### Installations
- Media picker, like in Signage playlist, will show the duration for newly uploaded videos when picked
  ![](/assets/20240511/media-picker.png ":size=212 :no-zoom")

### User management v2
- Coming soon, it's currently in private mode and will be available to public in within May 2024
- Better user management UI that uses more advanced and simpler user management APIs

## 2024-05-09

### User permissions
- Security improvements

## 2024-05-08

### Analytics dashboards
- Support images analytics card for device, space, and tenant level analytics dashboards
- Update your gridapp dependency `@ombori/grid-reports` to `3.91.6` or higher. Or simply do `yarn add @ombori/grid-reports@latest`
- [See more](/packages/javascript/grid-reports?id=images-card) to configure your gridapp analytics-schema to show images analytics card

## 2024-05-07

### Installations
- After a version upgrade, automatically enable the removal of any additional properties or values of properties that exist in the older version of the app but are not present in the newer version. This is initially auto-enabled for IoT or Edge app type installations. We'll enable for other types soon.

## 2024-05-06

### Analytics
- Fixed spaces list limit causing incorrect analytics count

### User Management
- Introduced User management tab in tenant Menu
- Moved `Menu > Users` to `Menu > User management > Users`
- Moved `Menu > User roles` to `Menu > User management > User roles`

## 2024-04-23

### Installations
- Fixed the associated installations list of a device when connected and disconnected to multiple IoT type installations
- Fixed newly added device to be immediately visible in Installations -> Devices list

## 2024-04-19
Changes around permissions are UI only. The APIs already allow or block these operations based on the permissions associated to the user role.

### Installations
- hide save button for users with no installation update permission (i.e. viewer role) in installation's global, space, and device settings pages
- Show alert message in installation's global, space, and device settings pages, for users with no installation update permission (i.e. viewer role) 
- change the label from "Edit" to "View" when user has no installation update permission
- allow delete only for users with installation delete permission

### Builds
- hide delete option when user has no permission to remove a build (i.e viewer role)
- hide app build link for non-pwa and non-mobile-pwa type installations (i.e. edge app installations)
- show deployment environments but disable deploy button when a user has no permission to remove a build (i.e viewer role)

### Devices
- Make tunnel links only visible to users with device update permission
- Hide delete button when user has no device delete permission

### Networking - Network Whitelist
- Allow settings update to only users with network whitelist update permission

## 2024-04-18
### Installations
- Added delete button on installations with settings overriding mode enabled

### Devices
- Fixed data residency value on provisioning for all regions

### Analytics Dashboards
- Preserve selected datetime range when navigating to different parts of the console and back to analytics page
  - The selected datetime range is only persisted within a browser tab

## 2024-04-11-A
### Spaces
- Fixed users list in space page showing user role id instead of display name

## 2024-03-01 - 2024-03-28
### Alerts
- Improved alerts UI
- Added support for analytics-based alerts

### Devices
- Added External ID property on device settings
- Fixed duplicate serial error on device connect/add
- Made tunnel link from console work for all GridOS and Phyos versions
- Improved CLI shell session inactivity timeout. See more Phygrid CLI updates: [here.](/cli/releasenotes)

### Spaces
- Able to search spaces on the "Parent" space field in create/update space form

### Environments
- Disallow `prod` environment to be deleted

### Marketplace
- Marketplace improvements
- Added more apps in the marketplace, like lift and learn
- Updated marketplace solutions descriptions

### Networking
- Menu > Networking
- Introduced whitelist control. This is used to filter or allow/disallow requests from Phyos 3 devices to the cloud. All required hostnames to integrate with the Phygrid cloud are whitelisted under the hood by default. Only custom hostnames that your custom apps are using should be added in the list.
- Check `Allow all` to allow all requests to the cloud from your devices, under your tenant 

## 2023-11-13
### Reports
- Ability to show Sesame succesrate and Store breakdown card in the console tenant dashboards

## 2023-11-03
### Reports
- Ability to show Sesame succesrate and SCO breakdown card in the console device dashboards

## 2023-09-25
### Reports
- Ability to show events list count card in the console installation dashboards
- Ability to show events list count based on events and additional data 
- [Reference documentation EventsList card](http://localhost:3000/#/packages/javascript/grid-reports?id=eventslist-card)

## 2023-08-29
### Media
- Region-based media storage
- Media upload improvements
- Grid Media Converter v2 - an Ombori developed and managed service to convert uploaded media to an optimized version for all supported HWs across the platform

### Devices
- Introduction of device bundles. A separate documentation will be released before production deployment. It's generally about better device components management.
- Outdated device components logic improvements

### Deployments
- Ability to rollback installation settings from a previous state. Right now you can only rollback builds, but not the settings value in the forms.

### Installation
- Added link to marketplace application from the installation page, below the installation name.

### Marketplace
- Fixed gridapp version action button visibility on safari browser

### Media Content Scheduler
- Built API endpoints for content channel CRUD
- Built API endpoints for content segment CRUD
- Built API endpoints for content tag CRUD

## 2023-08-28
### Tenant
- Ability to see and copy tenant slug, name, and ID on tenant name hover or click
- If you want to switch tenants, click the switch icon

### Installation
- Show language switcher for the Settings overriding mode or layout when multi-language support is enabled

### Devices
- Tunnel links manual create, edit, delete and connect
- Tunnel link hierarchy (parent-child relationship)
- Able to create tunnel links for GridOS devices

## 2023-08-11
### Installations
- Hide the API or Boot version field in installation `Settings` form
  - The build system will automatically detect and use the latest stable boot version on build time
  - Existing builds will not be affected
  - The stable boot version will be managed by OmboriGrid, who will also guarantee backward compatibility
- New Build or release page. A dedicated page which shows the information of an installation build. Go to installation > builds > select a build
- Improved version dropdown picker UI

### Reports
- Ability to pick previous dates beyond 60days from the current date. Before it was not possible.
- Limit the maximum date range that can be selected up to 60 days

### Devices
- Removed RPI4 in the device type options in the Device Set-up form. Please use Giada DN74 for rpi4 alternative.
- Existing RPI4 will not be affected. It will continue to run and will receive updated contents. Adding new one is not anymore possible.
- Added [GridOS Giada DN74](/general/hardware-requirements?id=giada-dn74) in the device type options in the Device Set-up form.

## 2023-07-24
### Reports
- Ability to show events count card in the console dashboards
- Ability to show events count breakdown per space
- [Reference documentation EventsCount card](http://localhost:3000/#/packages/javascript/grid-reports?id=eventscount-card)

## 2023-07-12
### GridApps
- Fix issue which uses older versions of app on install from the marketplace

### Devices
- Fix outdated version logic for associated device installation

## 2023-07-11
### Data export
- Fix permissions in console UI
- [Reference documentation for Data export](https://developer.omborigrid.com/#/grid-reports/raw-data-export) is also released

### Spaces
- Renamed `Locations` to `Spaces` in console UI labels
- Introduced nested spaces
- Able to select a parent of a space in settings form
- Added space type field. "Location" | "Section" | "Floor" | "Custom"
- This will support apps with reports that need to show breakdown per space (example, per SCO) in the installation level. Separate documentation will be released.

  ![](/assets/20230711/nested-spaces.png ":size=512 :no-zoom")

### Devices
- Able to see which device components need some actions in the device list and device page

  ![](/assets/20230711/device-outdated-versions.png ":size=360 :no-zoom")

### Reports
- EventsCount card UI fixes

### Widgets
- Space picker field
- `ui:options` support for ts-schema library

## 2023-07-03
### Alerts
- App Analytics based alerts
- Added `Device daily analytics session count` alert rule condition type
- Ability to get daily notifications for devices which do not meet the specified analytics session count threshold, in the previous day
- Added "Is enabled" column in the rules list view
- Hide smsRecipients field until sms cost/billing clarified

## 2023-06-29
### Alerts
- Menu -> Alerts
- Configurable device alerts
- Grid Alerts v2
- Separate documentation will be released soon

### Tenant settings
- Tenant level settings
- This can be used as a global reference for all installations
- Separate documentation will be released

### omg-devices service
- Updated omg-devices service for Grid alerts support

## 2023-06-05
### Menu
- Menu -> Data export
- Ability to export analytics raw data of your tenants through console and APIs with developer token

## 2023-06-01
### Analytics Data Export
- Menu -> Data export
- Ability to export analytics raw data of your tenants through console and APIs with developer token

### Alerts (Private Early Access)
- Menu -> Alerts
- Ability to configure device and application based alert rules and alert actions
- This will be enabled for everyone in first week of June

### Spaces
- Ability to delete a space from space page
- Prevent a space to be deleted when there are associated devices or mobile endpoints

## 2023-05-04

### Installations and Analytics Dashboards
- Date from and date to support for the monitoring status history widget support

## 2023-05-03

### Device Service
- Better approach in saving device status change history for monitoring
- Device and module twin realtime updates

### Schema Forms
- Fix queue picker schema to use correct queue api link for IN region

## Installation and Analytics Dashboards
- grid-signals and omg-reports based 24hour monitoring status widget
- better settings overriding form handling for array fields

## 2023-04-24

### Media Library
- ⭐ Free AI Generated Images powered by OpenAI's DALL-E. This can be used for example in your application content.
- ⭐ Free photo and video collections. This can be used for example in your digital signages with product templates, as a background photo or video.
- Explore the new features in your tenant page `Menu > Media` page

## Installation and Analytics Dashboards
- grid-signals and omg-reports based real-time monitoring status support

### Devices
- Hotfixes

## 2023-04-03

### Tenant branding
- New feature
- Tenant level branding and settings that can be referenced on installations' settings

### Products UI v2
- An improved products UI page in console where you can view, create, edit, and delete products.

### Installations
- Settings overriding scope indicator support for all ui fields and widgets

## 2023-03-22

### Installations
- Settings overriding MVP release (private access). General availability within March 2023.
- Settings overriding support for screen and edge installation types
- Settings v2 switch
- Settings overriding overriden field indicator
- Fixed incorrect settings applied to edge app installation devices on deploy
- Settings v2 save and auto-publish to selected env
- Settings v2 save and manual deployment
- Settings overriding fix count of overriden fields
- Bug fixes

## Marketplace
- Make Tasks App visible to all admin users of OmboriGrid console
- Able to install tasks app from marketplace as an Admin

## Devices
- Add Tizen divce type on the device creation form

## 2023-02-22

### Installations
- Settings overriding ui and releases (or builds)
- Better installations builds UI

`Note`: Settings overriding is currently in early access. It will be available to all tenants by the end of February 2023, as an opt-in feature for several weeks. It will then  be rolled out as the new installation settings page in 2nd week of March 2023. Contact Ombori to schedule a special workshop.

### Marketplace 
- Prices ui fixes

## 2023-02-12
### Queue App and Installations
- Updated api for `AU` data residency to a new ISO compliant infrastructure
- All queue APIs for other data residencies will be migrated soon. We will share an advanced notice and instructions for affected customers.

## 2023-01-26
### Installation group
- Able to edit an installation group, except "My installations".
- Able to delete installation group. A group cannot be removed if there are installations under it

### Device lease
- Ability to [Lease a device](/console/device-lease/)
- Device lease is available for tenant Admins

### Analytics dashboards
- reports and dashboards ui improvements

### Marketplace
- prices logic improvements

## 2023-01-03

### Locations
- Fixed locations list which had max 50 shown. It should show all locations on the side bar now under `Locations` tab


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
