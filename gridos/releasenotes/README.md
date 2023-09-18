# Grid Device Bundles and GridOS Release Notes

A Grid Device Bundle is a cutting-edge, flashable image specifically designed for AMD and Giada DN74 architectures. The image contains a GridOS, a robust operating system, and comes with pre-loaded edge applications or Docker images, for seamless and ready-to-deploy edge solutions.

[Read more about device bundles.](/gridos/device-bundles/)

## `Beta versions`

### Direct Download Link
- [Download Device bundle v1.0.7 for amd64-based devices](http://os.omborigrid.com/griddevice.1.0.7.amd64.img.xz)

- [Download Device bundle v1.0.7 for Giada dn74-based devices](http://os.omborigrid.com/griddevice.1.0.7.dn74.img.xz)

### Network Requirements
This version requires different IP addresses to be whitelisted on a network with firewall. [See network requirements for GridOS2.X.](/general/network-requirements?id=gridos-v2)

### Change log
- Introduced [Grid Device Bundles](/gridos/device-bundles/)
- Ubuntu 23.04 base
- Better and more reliable Grid Tunnel pre-loaded on the device
- Grid Edge runtime. An Ombori developed edge runtime as a substitute to Microsoft's edge runtime. The device is still using IoT Hub under-the-hood. It was built to have more control and stability of the edge runtime.
- Pre-loaded edge, agent, and screen modules
- Bug fixes

## `v1.2.1 (Stable Release for x86-64 arch)`
### Direct Download Link
- [Download GridOS v1.2.1 for Intel NUC devices (amd64-based devices)](http://os.omborigrid.com/gridos.1.2.1.amd64.img.xz)

### Change log
- Fixed incorrect serial number shown on provisioning screen
- Fixed a bug in the flash disk removal step on fresh GridOS installation
- Fixed network configuration bugs
- Added GridOS UI based Multi ethernet port configuration
- Updated embedded screen and agent modules
- Added support for open wifi network

## `v1.0.3 (Stable Release)`

### Direct Download Links
- [Download GridOS v1.0.3 for Intel NUC devices (amd64-based devices)](http://os.omborigrid.com/gridos.1.0.3.amd64.img.xz)
- [Download GridOS v1.0.3 for Raspberry Pi 4 (arm64-based devices)](https://os.omborigrid.com/gridos.1.0.3.rpi.img.xz)
- [Download GridOS v1.0.3 for Surface Go and Pro](http://os.omborigrid.com/gridos.1.0.3.surface.img.xz)

#### Instructions
For new devices, you can immediately download the GridOS from the above direct links and follow the instructions on the screen or cli during the installation.

For existing GridOS devices, you need to update below modules.

- Update `Screen module version to v3.1.0 or higher`
- Update `Ombori Agent module version to v1.8.9 or higher`

  ![](/assets/v1.0.3/gridos-v1.0.3-modules.png ":size=300 :no-zoom")

#### Over-the-air (OTA) Update 
You can update your existing GridOS Device over-the-air, through `Ombori Agent` module.

*WARNING: If the existing device is connected to a network with firewall or network whitelist, you need to add the IP addresses, [from this link](/gridos/set-up/v1/?id=network-whitelisting), based on your tenant residency. Additionally, make sure you have tested the new GridOS on the same hardware model before updating any production devices. You don't need to upgrade existing devices, if you don't have any reasons to do so. Existing devices running 0.9.X will still be supported long term, until further notice.*

- For amd64-based devices (i.e. Intel NUC), OTA update from v0.9.5 to v1.0.3 is supported. You can rollback to v0.9.5 when you need to.

- For rpi4 devices, OTA update from v0.9.4 to v1.0.3 is supported. You can rollback to v0.9.4 when you need to.

#### Features
- [Hidden Wifi Support](/gridos/set-up/v1/?id=hidden-wifi)
- [Better network configuration support](/gridos/set-up/v1/?id=network-whitelisting)
- Based on Ubuntu 22.04
- Improved provisioning interface
- Improved provisioning security
- Embedded core modules, Screen and Ombori Agent, for faster boot-up time and less initial required resources to download

## v1.1.0 (Beta)
#### Features
- [Hidden Wifi Support](/gridos/set-up/v1/?id=hidden-wifi)
- [Download GridOS v1.1.0](http://os.omborigrid.com/gridos.1.1.0.amd64.img.xz)
