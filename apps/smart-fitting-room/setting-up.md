# Setting up Smart Fitting Room

## Installation

![](/assets/sfr-marketplace.png ":no-zoom :size=400")

To set up a Smart Fitting Room screen, go to Marketplace > Apps.

![](/assets/sfr-install.png ":no-zoom :size=400")

Search for `smart-fitting-room` app from the list and click `Install`

![](/assets/sfr-install-form.png ":no-zoom :size=400")

Fill out the popup form with the installation name and installation group based on how you want it organized

## Configuration

Now you've completed the installation, it's time to configure it. 
First, find your installation in the sidebar where you've installed it. 

Once you've opened it you can configure your Smart Fitting Room application. 

As a start, go to "Settings" tab and make sure to set the following:
![](/assets/sfr-grid-settings.png ":no-zoom :size=700")
- **Release**: Should be GridApp v2.170.0 or above (latest version as much as possible)
- **Supported Languages**
- **Default Language** - will be used by the application (we support 1 language for now on app usage)


You can then start with [adding content](/apps/smart-fitting-room/adding-content.md), or you can start by [adding a device](/general/adding-device.md).

## Device Setup Instructions

After adding content and configurations above are done, here are important steps to assure that correct data is being loaded to the kiosks/devices.

![](/assets/device-settings.png ":no-zoom :size=700")
- Make sure that `Environment` of the device matches with the environment in Grid Products where you pushed your data
- Make sure that `Location` of the device matches the equivalent `spaceIds` and `spaceId` fields from [Grid Products](/grid-products/data-model.md?id=gridproduct) model that you pushed. Grid Products will filter down the products returned based on the device's Space (id).
