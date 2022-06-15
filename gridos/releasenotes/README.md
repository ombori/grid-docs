# GridOS Release Notes

## v1.0.3 (Stable Release)

### Direct Download Links
- [Download GridOS v1.0.3 for Intel NUC devices (amd64-based devices)](http://os.omborigrid.com/gridos.1.0.3.amd64.img.xz)
- [Download GridOS v1.0.3 for Raspberry Pi 4 (amd64-based devices)](http://os.omborigrid.com/gridos.1.0.3.amd64.img.xz)
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
- [VPN Support](/gridos/set-up/v1/?id=network-whitelisting)
- Based on Ubuntu 22.04
- Improved provisioning interface
- Improved provisioning security
- Embedded core modules, Screen and Ombori Agent, for faster boot-up time and less initial required resources to download

## v1.1.0 (Beta)
#### Features
- [Hidden Wifi Support](/gridos/set-up/v1/?id=hidden-wifi)
- [Download GridOS v1.1.0](http://os.omborigrid.com/gridos.1.1.0.amd64.img.xz)
