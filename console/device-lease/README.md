# Device Lease

Device lease is a feature to temporarily move a device from tenantA to tenantB for a specific period of time. It can be used when you need to test an installation in tenantB, but the device is in tenantA.

- Billing - while the device is leased in tenantB, the device usage will still be billed against the owner tenantA.
- Settings and contents - the device will acquire the installation settings and contents in tenantB, while being leased.
- Expiry - the device will be automatically moved back to tenantA by the system after the lease expires. It will restore the device settings to the state before it was leased.

Device lease is a feature developed for users managing multiple tenants. Generally this can be helpful for Certifified Solution Providers (CSPs) and enterprise users.

### Leasing a device

- To lease a device, go to the device page.

  ![](/assets/device-lease-button.png ":size=360 :no-zoom")

- Set the desired tenant and installation name, where you want to temporirily move and lease the device.

  ![](/assets/device-lease-form.png ":size=360 :no-zoom")