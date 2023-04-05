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

# Installation Instructions
There are some devices which need special steps to configure during installation. Soon, these special steps will be included in our core releases.

## Elo i2 15"
Elo i2 devices require additional configuration for black screen issues.

```
cd ~
sudo git clone https://github.com/ombori/omb-elo-i2-15-fix
cd KMS-FixForBlackScreen
sudo bash fix_blackscreen.sh
```

## Tizen 4.X (Deprecated)
Tizen 4.X can still run on the platform, but we are not developing new features for it.

To add a Tizen 4.X device, follow below instructions:
- In console, go to installation > devices > connect device > set-up a new device
- In console, Select "Generic browser" type
- In tizen TV, go to URL launcher and input `http://tizen.omborigrid.com/2.170.0`
- In console, enter the 4 letter code
- Your device should be running the screen application after

## Tizen 6.5
Tizen 6.5 is currently supported in the OmboriGrid Platform.

To add a Tizen 6.5 device, follow below instructions:
- In console, go to installation > devices > connect device > set-up a new device
- In console, Select "Tizen" type. You will see the latest tizen URL for tizen6.5
- In tizen TV, go to URL launcher and input the specified URL. (example: `http://tizen.omborigrid.com/3.26.2`)
- In console, enter the 4 letter code
- Your device should be running the screen application after

### Tizen 6.5 remote supervisor version update
Remote tizen supervisor version is possible for tizen6.5 using omg cli

```
omg dev invoke <device> agent setUrl '{url: "http://some.new.url"}'
```

### Tizen 6.5 Playlist and Ticket Signage Support
To run playlist signage and ticket signage on Tizen 6.5 TV, you need to use the latest versions.

- API version (Boot version): `3.28.1`

  *API version can be found in `Installation > Settings` tab or `Installation > Settings > Global settings`

- Playlist Signage app version: `5.3.48`
- Ticket Signage app version: `0.5.39`



