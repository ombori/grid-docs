# Hardware requirements
Ombori Grid is very flexible in terms of hardware, however we have some minimum requirements for each hardware type. If you have any questions if certain hardware is supported in your specific case please contact us on [Slack](https://join.slack.com/t/slack-pgo5586/shared_invite/zt-s1ajca83-k8i1f2mqgCMD0vDfpCk4Bg).

Keep in mind all these specifications are minimum specifications, anything above would work as well.

## Intel
A wide variety of Intel CPU-based devices are supported by Ombori Grid and GridOS. When [adding the device](/general/adding-device/) just make sure to follow the Intel (NUC) installation guide.

Supported application types: Screen App, IoT App

**Minimum requirements**

- Intel Celeron Quad Core 1.5GHz
- 10GB disk space
- 4GB RAM

Example devices: Intel NUC, Intel Compute Stick, Surface Go, Surface Pro, and many more.

## Raspberry Pi
Raspberry Pi 4 is supported by Ombori Grid and GridOS.

Supported application types: Screen App, IoT App

**Minimum requirements**
- Raspberry Pi 4 4GB
- SD Card A2. Read Speed > 150MB/s. Write Speed > 60MB/s
- Heatsink case with fans

A heatsink is not strictly required, but recommended. Depending on what will be running on RPI, the hardware can potentially get hot.

## Samsung Smart Signage Display
The Samsung Smart Signage displays allow you to run Screen Apps, like Signage Playlist.

Supported application types: Screen App

**Minimum requirements**

- Samsung Tizen v3.5 or above

## Android Tablets
Android Tablets are great for all kinds of kiosk-like experiences.

Supported application types: Screen App

**Minimum requirements**

- 8GB disk space
- 2GB RAM
## Android TVBox
Android TVBox is capable of running apps on any screen you have in stock.

Supported application types: Screen App

**Minimum requirements**

- 8GB disk space
- 2GB RAM

# Installation Instructions
There are some devices which need special steps to configure during installation. Soon, these special steps will be included in our core releases.

## Elo i2 15"
Elo i2 devices require additional configuration for black screen issues.

```
cd ~
sudo git clone https://github.com/ugur-ombori/KMS-FixForBlackScreen.git
cd KMS-FixForBlackScreen
sudo bash fix_blackscreen.sh
```

## Tizen 6.5
Tizen 6.5 devices should use the latest Firmware

Example for QM43B, download the latest Firmware from the [samsung support website](https://displaysolutions.samsung.com/support/resources/product-support/QM43B).

You can check how to update your tizen devices to the latest firmware in the [samsung support website](https://www.samsung.com/us/support/answer/ANS00062224/).
