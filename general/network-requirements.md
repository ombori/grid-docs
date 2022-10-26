# Network Requirements
All devices connected to the Ombori Grid need to have access to the internet to receive updates. However, they can work offline after the first launch.

## Offline support
For Screen Apps, you need to connect to the internet at least once to download content and assets. All apps, assets, and web resources will be downloaded on first launch, and will function offline as soon as the content has been downloaded. Of course, internet-based functionality will be suspended until the device is connected once again.

Once the device is connected to the internet after a time of being offline, a sync will take place to update according to the console.
## Whitelist
To accepting inbound requests from Ombori Grid to your APIs, you need to whitelist the following IP addresses, based on your tenants Data Residency

Unless otherwise specified, all domains are using port `443`.

#### Global (required for all data residencies)
| IP Address      |
| --------------- |
| 20.91.176.195   |
| 20.240.8.184    |
| 20.103.188.246  |
| 20.103.191.105  |

#### AU
| IP Address      |
| --------------- |
| 20.193.43.178   |
| 20.193.43.210   |
#### EU
| IP Address      |
| --------------- |
| 20.240.25.169   |
| 20.240.25.198   |
#### India
| IP Address      |
| --------------- |
| 20.207.65.55    |
| 20.204.234.88   |
#### UAE
| IP Address      |
| --------------- |
| 20.203.77.64    |
| 20.203.77.62    |
#### US
| IP Address      |
| --------------- |
| 20.232.86.63    |
| 20.121.248.244  |


### GridOS v1+

For devices which are running GridOS v1.0.3 or higher, you need to whitelist the following IP addresses, based on tenants data-residency to establish connectivity to the Ombori Grid.

#### AU
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.211.138.232  | 443 | UDP        | Post-provisioning  |
#### EU
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.126.185.169  | 443  | UDP        | Post-provisioning |
#### IN
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.219.43.36    | 443  | UDP        | Post-provisioning |

#### UAE
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.233.13.206   | 443  | UDP        | Post-provisioning |

#### US
| IP Address      | Port | Porotocol  | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | UDP        | Provisioning      |
| 20.121.94.131   | 443  | UDP        | Post-provisioning |



### Queue Management European Union

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| ombori-queue-prod-eu.azure-api.net    | Queues EU API                        |
| queue.eu.ombori.com                   | Queue Curbside EU                    |
| signalr-prod-eu-1.service.signalr.net | SignalR EU                           |
| signal-eu.omborigrid.com              | Grid Signals                         |
| realtime-eu.omborigrid.com            | Grid Signals - Realtime events       |
| analytics.omborigrid.com              | Analytics Service                    |


### Queue Management United States

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| ombori-queue-prod-us.azure-api.net    | Queues US API                        |
| queue.us.ombori.com                   | Queue WebUI US                       |
| signalr-prod-us.service.signalr.net   | SignalR US                           |
| signal-us.omborigrid.com              | Grid Signals                         |
| realtime-us.omborigrid.com            | Grid Signals - Realtime events       |
| analytics.omborigrid.com              | Analytics Service                    |

### Queue Management Australia

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| ombori-queue-prod-au.azure-api.net    | Queues AU API                        |
| queue.au.ombori.com                   | Queue WebUI US                       |
| signalr-prod-au.service.signalr.net   | SignalR AU                           |
| signal-au.omborigrid.com              | Grid Signals                         |
| realtime-au.omborigrid.com            | Grid Signals - Realtime events       |
| analytics.omborigrid.com              | Analytics Service                    |

### Queue Management United Arab Emirates

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| ombori-queue-prod-uae.azure-api.net   | Queues UAE API                       |
| queue.uae.ombori.com                  | Queue Curbside UAE                   |
| signalr-prod-uae.service.signalr.net  | SignalR UAE                          |
| signal-uae.omborigrid.com             | Grid Signals                         |
| realtime-uae.omborigrid.com           | Grid Signals - Realtime events       |
| analytics.omborigrid.com              | Analytics Service                    |

### Queue Management India

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| ombori-queue-prod-in.azure-api.net    | Queues IN API                        |
| queue.in.ombori.com                   | Queue Curbside IN                    |
| signalr-prod-in.service.signalr.net   | SignalR IN                           |
| signal-in.omborigrid.com              | Grid Signals                         |
| realtime-in.omborigrid.com            | Grid Signals - Realtime events       |
| analytics.omborigrid.com              | Analytics Service                    |

### General
- For Tizen, android and other device type other than GridOS v1 based devices

| Domain                                               | Description                          |
| ---------------------------------------------------- | ------------------------------------ |
| app.omborigrid.com                                   | Gridapp Releases                     |
| storage.googleapis.com                               | Google Workbox                       |
| media.omborigrid.com                                 | Gridapp media                        |
| browser-api.prod.omborigrid.com                      | Browser API                          |
| tts-proxy.northeurope.cloudapp.azure.com             | TTS Service                          |
| o190418.ingest.sentry.io                             | Sentry Error Reporting               |
| analytics.omborigrid.com                             | Analytics Service                    |
| api.omborigrid.com                                   | Grid API                             |
| qr.run                                               | URL Shortener Service                |
| installations-service.omborigrid.com                 | Grid Installations Service           |
| tizen.omborigrid.com                                 | Grid Tizen Supervisor                |
| gridhealth.blob.core.windows.net                     | Screenshot and device status service |
| signal-au.omborigrid.com                             | Grid Signals Prod Australia          |
| signal-eu.omborigrid.com                             | Grid Signals Prod Europe             |
| signal-in.omborigrid.com                             | Grid Signals Prod India              |
| signal-uae.omborigrid.com                            | Grid Signals Prod UAE                |
| signal-us.omborigrid.com                             | Grid Signals Prod United States      |
| realtime-au.omborigrid.com                           | Grid Signals - Realtime events       |
| realtime-eu.omborigrid.com                           | Grid Signals - Realtime events       |
| realtime-in.omborigrid.com                           | Grid Signals - Realtime events       |
| realtime-uae.omborigrid.com                          | Grid Signals - Realtime events       |
| realtime-us.omborigrid.com                           | Grid Signals - Realtime events       |
