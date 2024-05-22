# Devices
Devices in console can be added to a Screen or Edge/Iot installation types. You can manage the devices through console and see the telemetry and device components statuses.

## Device Status
A device can have different statuses reported in console.

| Status name               |  Status value   | Description                                                                           | Possible Cause                                                  |
|---------------------------|-----------------|---------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| Online                    | ok              | Device reported healthy status of all its components                                  | -                                                               |
| Offline                   | offline         | Device is disconnected from the Grid Platform in the cloud                            | Network issue                                                   |
| Runtime not responding    | noedge          | Device is disconnected from the Grid Platform                                         | Network issue, phyedged, Grid Device Service                    |          
| No cloud connection       | nohub           | edgeHub is not reported in the telemetry                                              | Phyedged, Azure iothub                                          |
| Screen not responding     | noscreen        | When connected to a screen installation and no screen is detected in HDMI port        | Screen is off, HDMI connection, screen module                   |
| Agent not responding      | noagent         | edgeAgent is not reported in the telemetry                                            | Network issue, phyedged, Grid Device Service, Azure iothub      | 
| No screenshot             | noshot          | When connected to a screen installation and last screenshot is > 6mins                | Screen module, Grid Device health storage                       | 
| No reboot                 | noreboot        | When device auto daily reboot failed and device did not reboot for more than 24hours  | Phyagent, device agent module settings                          |
| Updating                  | updating        | When a device component is being updated, or when an edge app is updating             | New deployed edge installation configurations                   |
| App not running           | backoff         | When an edge app or device component is crashing or unable to start                   | Edge app, Phyedged, Phyagent                                    |

## Device Lease

Device lease is a feature to temporarily move a device from tenantA to tenantB for a specific period of time. It can be used when you need to test an installation in tenantB, but the device is in tenantA.

- Billing - while the device is leased in tenantB, the device usage will still be billed against the owner tenantA.
- Settings and contents - the device will acquire the installation settings and contents in tenantB, while being leased.
- Expiry - the device will be automatically moved back to tenantA by the system after the lease expires. It will restore the device settings to the state before it was leased.

Device lease is a feature developed for users managing multiple tenants. Generally this can be helpful for Certified Solution Providers (CSPs) and enterprise users.

#### Leasing a device

- To lease a device, go to the device page.

  ![](/assets/device-lease-button.png ":size=360 :no-zoom")

- Set the desired tenant and installation name, where you want to temporirily move and lease the device.

  ![](/assets/device-lease-form.png ":size=360 :no-zoom")