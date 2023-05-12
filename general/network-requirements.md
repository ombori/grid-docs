# OmboriGrid Network Requirements

This document outlines the network requirements for devices connected to the Ombori Grid. It includes information about offline support, IP whitelisting, and domain-specific configurations.

## Table of Contents

- [Offline Support](#offline-support)
- [Standard Configuration](#standard-configuration)
  - [GridOS v1+](#gridos-v1)
    - [Australia](#au-1)
    - [European Union](#eu-1)
    - [India](#in)
    - [United Arab Emirates](#uae-1)
    - [United States](#us-1)
- [Employee Tools and Queue Management](#employee-tools-and-queue-management)
  - [European Union](#queue-management-european-union)
  - [United States](#queue-management-united-states)
  - [Australia](#queue-management-australia)
  - [United Arab Emirates](#queue-management-united-arab-emirates)
  - [India](#queue-management-india)
- [Other Browser-Based Devices](#other-browser-based-devices)
- [Advanced Scenario: Firewall Openings for Internal System Integration](#advanced-scenario-firewall-openings-for-internal-system-integration)
  - [Global (required for all data residencies)](#global-required-for-all-data-residencies)
  - [Australia](#au)
  - [European Union](#eu)
  - [India](#india)
  - [United Arab Emirates](#uae)
  - [United States](#us)
## In-store Devices Firewall Configuration
### Offline Support

For Screen Apps, devices must connect to the internet at least once to download content and assets. All apps, assets, and web resources will be downloaded on first launch and will function offline once the content has been downloaded. Internet-based functionality will be suspended until the device is connected again. A sync will take place to update according to the console when the device reconnects to the internet after being offline.

### GridOS v1+

For devices running GridOS v1.0.3 or higher, whitelist the following IP addresses based on tenant's data-residency to establish connectivity to the Ombori Grid.

#### Australia
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | TCP & UDP  | Provisioning      |
| 20.211.138.232  | 443  | TCP & UDP  | Post-provisioning |

#### European Union
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | TCP & UDP  | Provisioning      |
| 20.126.185.169  | 443  | TCP & UDP  | Post-provisioning |

#### India
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | TCP & UDP  | Provisioning      |
| 20.219.43.36    | 443  | TCP & UDP  | Post-provisioning |

#### United Arab Emirates
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | TCP & UDP  | Provisioning      |
| 20.233.13.206   | 443  | TCP & UDP  | Post-provisioning |

#### United States
| IP Address      | Port | Protocol   | Description       |
| --------------- |----- | ---------- | ----------------  |
| 20.103.183.92   | 443  | TCP & UDP  | Provisioning      |
| 20.121.94.131   | 443  | TCP & UDP  | Post-provisioning |

### Employee Tools and Queue Management

For employee devices that work with the OmboriGrid productivity and clienteling tools, the following domains need to be whitelisted in your firewall.

#### United States

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| api.omborigrid.com                    | OmboriGrid API                       |
| screen.omborigrid.com                 | OmboriGrid Screen Apps               |
| queue-us.ombori.com                   | Employee Queue Web UI US Region      |
| tasks-us.ombori.com                   | Employee Task Web UI US Region       |
| realtime-us.omborigrid.com            | OmboriGrid Realtime Channel          |
| analytics.omborigrid.com             | Analytics Service                     |

#### European Union

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| api.omborigrid.com                    | OmboriGrid API                       |
| screen.omborigrid.com                 | OmboriGrid Screen Apps               |
| queue-eu.ombori.com                   | Employee Queue Web UI EU Region      |
| tasks-eu.ombori.com                   | Employee Task Web UI EU Region       |
| realtime-eu.omborigrid.com            | OmboriGrid Realtime Channel          |
| analytics.omborigrid.com             | Analytics Service                     |

#### Australia

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| api.omborigrid.com                    | OmboriGrid API                       |
| screen.omborigrid.com                 | OmboriGrid Screen Apps               |
| queue-au.ombori.com                   | Employee Queue Web UI AU Region      |
| tasks-au.ombori.com                   | Employee Task Web UI AU Region       |
| realtime-au.omborigrid.com            | OmboriGrid Realtime Channel          |
| analytics.omborigrid.com              | Analytics Service                     |

#### United Arab Emirates

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| api.omborigrid.com                    | OmboriGrid API                       |
| screen.omborigrid.com                 | OmboriGrid Screen Apps               |
| queue-uae.ombori.com                  | Employee Queue Web UI UAE Region     |
| tasks-uae.ombori.com                  | Employee Task Web UI UAE Region      |
| realtime-uae.omborigrid.com           | OmboriGrid Realtime Channel          |
| analytics.omborigrid.com              | Analytics Service                     |

#### India

| Domain                                | Description                          |
| ------------------------------------- | ------------------------------------ |
| api.omborigrid.com                    | OmboriGrid API                       |
| screen.omborigrid.com                 | OmboriGrid Screen Apps               |
| queue-in.ombori.com                   | Employee Queue Web UI IN Region      |
| tasks-in.ombori.com                   | Employee Task Web UI IN Region       |
| realtime-in.omborigrid.com            | OmboriGrid Realtime Channel          |

### Other browser-based devices
For devices such as Tizen, Android, third-party digital signage systems, or any other device utilizing OmboriGrid Screen applications within a web browser, the following firewall configurations are necessary:

| Domain                                               | Description                          |
| ---------------------------------------------------- | ------------------------------------ |
| app.omborigrid.com                                   | Gridapp Releases                     |
| storage.googleapis.com                               | Google Workbox                       |
| media.omborigrid.com                                 | Gridapp media                        |
| tts-proxy.northeurope.cloudapp.azure.com             | TTS Service                          |
| o190418.ingest.sentry.io                             | Sentry Error Reporting               |
| analytics.omborigrid.com                             | Analytics Service                    |
| api.omborigrid.com                                   | Grid API                             |
| qr.run                                               | URL Shortener Service                |
| installations-service.omborigrid.com                 | Grid Installations Service           |
| tizen.omborigrid.com                                 | Grid Tizen Supervisor                |
| gridhealth.blob.core.windows.net                     | Screenshot and device status service |
| realtime-au.omborigrid.com                           | Grid Signals - Realtime events       |
| realtime-eu.omborigrid.com                           | Grid Signals - Realtime events       |
| realtime-in.omborigrid.com                           | Grid Signals - Realtime events       |
| realtime-uae.omborigrid.com                          | Grid Signals - Realtime events       |
| realtime-us.omborigrid.com                           | Grid Signals - Realtime events       |

## Advanced Scenario: Firewall Openings for Internal System Integration

In advanced scenarios where OmboriGrid needs to communicate with internal retailer systems, such as querying inventory and product information APIs, you may need to open specific firewall ports to allow inbound traffic from OmboriGrid. This is not our standard approach for integration and should only be used when necessary. In these cases, you should whitelist the following IP addresses, based on your tenant's Data Residency.


| IP Address    |
| ------------- |
| 20.91.176.195 |
| 20.240.8.184  |
| 20.103.188.246|
| 20.103.191.105|

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

#### IN
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


Please note that the specific ports and protocols used will vary depending on your internal system requirements. Consult your internal IT team for the appropriate configuration.
