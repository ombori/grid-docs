# Console Releasenotes
The [Ombori Grid Console](https://console.omborigrid.com) is being updated frequently. This page contains all the console changes that were deployed in production recently.

## 20210907-A

### Devices
- fixed device status
- put back "Failing" devices status. There are 2 possible cases when a device has failing status:
  - when the last screenshot of the device is > 6mins. It means that there is something wrong with the screen module. It can be resolved by making sure that your device has the latest screen module. Rebooting the device should also help to refresh the module state.
  - when the device iotedge instance is online, but the screen module instance is offline. If you publish and deploy new app build, it might not get the latest build. If you have network firewall enabled, make sure that all [required Grid Domains](/concepts/network-requirements) are whitelisted. Rebooting the device should also help to refresh the module state.
- added the related installation name and installation link in the device details' page
  ![test](https://media.omborigrid.com/media/5cbac8a388e174147b878cdd/88891430-0ff2-11ec-8623-63e00804878d ":size=300")

### Subscriptions
- fixed subscription schema and azure saas subscription creation flow
- fixed payment method labels

## Old releases
You can find the old console releases in our old and deprecated [confluence portal](https://ombori.atlassian.net/wiki/spaces/OAKB/pages/582057985/Grid+Console+Releases).