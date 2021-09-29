# Network Requirements
All devices connected to the Ombori Grid need to have access to the internet to receive updates. However, they can work offline after the first launch.

## Offline support
For Screen Apps, you need to connect to the internet at least once to download content and assets. All apps, assets, and web resources will be downloaded on first launch, and will function offline as soon as the content has been downloaded. Of course, internet-based functionality will be suspended until the device is connected once again. 

Once the device is connected to the internet after a time of being offline, a sync will take place to update according to the console.
## Whitelist
There is a list of domains in use that require to be added to your internal whitelist in your firewall. We are unable to provide a static list of IP addresses as some Azure endpoints do not have static IP addresses.

Unless otherwise specified, all domains are using port `443`.

### General

| Domain                                               | Description                 |
| ---------------------------------------------------- | --------------------------- |
| app.omborigrid.com                                   | Gridapp Releases            |
| storage.googleapis.com                               | Google Workbox              |
| media.omborigrid.com                                 | Gridapp media               |
| iot-ca-prod.ombori.com                               | GridOS Provisioning Service |
| browser-api.prod.omborigrid.com                      | Browser API                 |
| omborigridregistry.azurecr.io                        | Modules Registry            |
| tts-proxy.northeurope.cloudapp.azure.com             | TTS Service                 |
| edge-stream-1.northeurope.cloudapp.azure.com         | IoT Edge                    |
| o190418.ingest.sentry.io                             | Sentry Error Reporting      |
| grid-admin-hub.azure-devices.net                     | Azure IoT Hub               |
| analytics.omborigrid.com                             | Analytics Service           |
| api.omborigrid.com                                   | Grid API                    |
| secops-iot-dps-prod-ca-srvc-010.azurewebsites.net    | Device Provisioning Service |
| secops-iot-dps-prod-alloc-srvc-010.azurewebsites.net | Device Provisioning Service |
| browser-connect.azurewebsites.net                    | Device Provisioning Service |
| qr.run                                               | URL Shortener Service       |
| os.omborigrid.com                                    | GridOS Updates              |
| installations-service.omborigrid.com                 | Grid Installations Service  |
| tizen.omborigrid.com                                 | Grid Tizen Supervisor       |


### Virtual Queues
For virtual queues we have a specific set of domains.

| Domain                                | Description    |
| ------------------------------------- | -------------- |
| ombori-queue-prod-eu.azure-api.net    | Queues EU API  |
| ombori-queue-prod-us.azure-api.net    | Queues US API  |
| ombori-queue-prod-au.azure-api.net    | Queues AU API  |
| ombori-queue-prod-uae.azure-api.net   | Queues UAE API |
| signalr-prod-eu-1.service.signalr.net | SignalR EU     |
| signalr-prod-us.service.signalr.net   | SignalR US     |
| signalr-prod-au.service.signalr.net   | SignalR AU     |
| signalr-prod-uae.service.signalr.net  | SignalR UAE    |
