# Network Requirements
All devices connected to the Ombori Grid need to have access to the internet to receive updates. However, they can work offline after the first launch.

## Offline support
For Screen Apps, you need to connect to the internet at least once to download content and assets. All apps, assets, and web resources will be downloaded on first launch, and will function offline as soon as the content has been downloaded. Of course, internet-based functionality will be suspended until the device is connected once again. 

Once the device is connected to the internet after a time of being offline, a sync will take place to update according to the console.
## Whitelist
There is a list of domains in use that require to be added to your internal whitelist in your firewall. We are unable to provide a static list of IP addresses as some Azure endpoints do not have static IP addresses.

Unless otherwise specified, all domains are using port `443`.

### GridOS v1

For devices which are running GridOS v1.0.3 or higher, you only need to whitelist following IP addresses, based on your region or data-residency.

#### EU
| IP Address      | Port | Protocol  | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.126.185.169  | 443  | UDP        | Post-provisioning |
| 20.126.162.189  | 443  | UDP        | Post-provisioning |

#### IN
| IP Address      | Port | Protocol  | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.219.43.36    | 443  | UDP        | Post-provisioning |

#### UAE
| IP Address      | Port | Protocol  | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.233.13.206   | 443  | UDP        | Post-provisioning |

#### US
| IP Address      | Port | Porotocol  | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.121.94.131   | 443  | UDP        | Post-provisioning |

#### AU
| IP Address      | Port | Protocol  | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.211.138.232   | 443 | UDP        | Post-provisioning |

### Queue Management
For Queue Management, we have a specific set of domains.

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| ombori-queue-prod-eu.azure-api.net    | Queues EU API                        |
| ombori-queue-prod-us.azure-api.net    | Queues US API                        |
| ombori-queue-prod-au.azure-api.net    | Queues AU API                        |
| ombori-queue-prod-uae.azure-api.net   | Queues UAE API                       |
| queue.us.ombori.com                   | Queue WebUI US                       |
| queue.eu.ombori.com                   | Queue Curbside EU                    |
| queue.uae.ombori.com                  | Queue Curbside UAE                   |
| signalr-prod-eu-1.service.signalr.net | SignalR EU                           |
| signalr-prod-us.service.signalr.net   | SignalR US                           |
| signalr-prod-au.service.signalr.net   | SignalR AU                           |
| signalr-prod-uae.service.signalr.net  | SignalR UAE                          |
| signal-qa.omborigrid.com              | Grid Signals QA                      |
| signal-au.omborigrid.com              | Grid Signals Prod Australia          |
| signal-eu.omborigrid.com              | Grid Signals Prod Europe             |
| signal-in.omborigrid.com              | Grid Signals Prod India              |
| signal-uae.omborigrid.com             | Grid Signals Prod UAE                |
| signal-us.omborigrid.com              | Grid Signals Prod United States      |
| grid-signal-au.service.signalr.net    | Grid Signals - SignalR Australia     |
| grid-signal-eu.service.signalr.net    | Grid Signals - SignalR Europe        |
| grid-signal-in.service.signalr.net    | Grid Signals - SignalR India         |
| grid-signal-uae.service.signalr.net   | Grid Signals - SignalR UAE           |
| grid-signal-us.service.signalr.net    | Grid Signals - SignalR US            |
| analytics.omborigrid.com              | Analytics Service                    |

### General

- For GridOS 0.9.5 or lower
- For Tizen, android and other device type other than GridOS v1 based devices

| Domain                                               | Description                          |
| ---------------------------------------------------- | ------------------------------------ |
| app.omborigrid.com                                   | Gridapp Releases                     |
| storage.googleapis.com                               | Google Workbox                       |
| media.omborigrid.com                                 | Gridapp media                        |
| iot-ca-prod.ombori.com                               | GridOS Provisioning Service          |
| browser-api.prod.omborigrid.com                      | Browser API                          |
| omborigridregistry.azurecr.io                        | Modules Registry                     |
| tts-proxy.northeurope.cloudapp.azure.com             | TTS Service                          |
| edge-stream-1.northeurope.cloudapp.azure.com         | IoT Edge                             |
| o190418.ingest.sentry.io                             | Sentry Error Reporting               |
| grid-admin-hub.azure-devices.net                     | Azure IoT Hub                        |
| analytics.omborigrid.com                             | Analytics Service                    |
| api.omborigrid.com                                   | Grid API                             |
| secops-iot-dps-prod-ca-srvc-010.azurewebsites.net    | Device Provisioning Service          |
| secops-iot-dps-prod-alloc-srvc-010.azurewebsites.net | Device Provisioning Service          |
| browser-connect.azurewebsites.net                    | Device Provisioning Service          |
| qr.run                                               | URL Shortener Service                |
| os.omborigrid.com                                    | GridOS Updates                       |
| installations-service.omborigrid.com                 | Grid Installations Service           |
| tizen.omborigrid.com                                 | Grid Tizen Supervisor                |
| omborigridregistry.westus.data.azurecr.io            | Module Repository Data (US)          |
| omborigridregistry.westeurope.data.azurecr.io        | Module Repository Data (EU)          |
| *.data.mcr.microsoft.com                             | IoT Edge Hub                         |
| mcr.microsoft.com                                    | IoT Edge Hub                         |
| gridhealth.blob.core.windows.net                     | Screenshot and device status service |
| signal-qa.omborigrid.com                             | Grid Signals QA                      |
| signal-au.omborigrid.com                             | Grid Signals Prod Australia          |
| signal-eu.omborigrid.com                             | Grid Signals Prod Europe             |
| signal-in.omborigrid.com                             | Grid Signals Prod India              |
| signal-uae.omborigrid.com                            | Grid Signals Prod UAE                |
| signal-us.omborigrid.com                             | Grid Signals Prod United States      |
| grid-signal-au.service.signalr.net                   | Grid Signals - SignalR Australia     |
| grid-signal-eu.service.signalr.net                   | Grid Signals - SignalR Europe        |
| grid-signal-in.service.signalr.net                   | Grid Signals - SignalR India         |
| grid-signal-uae.service.signalr.net                  | Grid Signals - SignalR UAE           |
| grid-signal-us.service.signalr.net                   | Grid Signals - SignalR US            |
| google.com:80                                        | Devices status in start QR screen    |
