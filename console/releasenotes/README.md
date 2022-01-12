# Console Release Notes
The [Ombori Grid Console](https://console.omborigrid.com) is being updated frequently. This page contains all the console changes that were deployed in production recently.

## 2021-01-07
### Installations
- Transferred Overview tab dashboard & its contents to Legacy Overview with same access constraints
- Repurposed Overview tab to contain initial tenant powerbi analytics (contents of analytics remain a work in progress)
- Add the Overview tab to other types of installations i.e. Queue or cloud-based installations

## 2021-09-10

### Devices
- Fixed a bug in the installation's list of devices

### Developers Tab
- Added developer's documentation link
- Added Developer's slack link

### Installations
- Moved the installation delete button
  - For queue installations, it is found in `Other configurations` tab
  - For screen, mobile, and IoT installation types, it is found in the `Settings` tab
- Fixed delete and publish button styles

### Marketplace
- Added Web Kiosk in the list of solutions
- Added Web Kiosk price

![](/assets/20210910-webkiosk.png ":size=300 :no-zoom")

### Billing
- Added the list of active plans. Today, it is only available for `sysadmin` role. It will be available for `admin` role in the future releases.


## 2021-09-07

### Devices
- Fixed device status
- Put back the "Failing" devices status. There are 2 possible cases when a device has a failing status:
  - When the last screenshot of the device is > 6mins. It means that there is something wrong with the screen module. It can be resolved by making sure that your device has the latest screen module. Rebooting the device should also help to refresh the module state.
  - When the device IoT Edge instance is online but the screen module instance is offline. If you publish and deploy a new app build, it might not get the latest build. If you have a network firewall enabled, make sure that all [required Grid Domains](/general/network-requirements) are whitelisted. Rebooting the device should also help to refresh the module state.
- Added the related installation name and installation link in the device details' page
![](/assets/20210907-related.png ":size=300 :no-zoom")

### Subscriptions
- Fixed subscription schema and azure saas subscription creation flow
- Fixed payment method labels

## Previous releases
You can find the previous console releases in our deprecated [Confluence portal](https://ombori.atlassian.net/wiki/spaces/OAKB/pages/582057985/Grid+Console+Releases).