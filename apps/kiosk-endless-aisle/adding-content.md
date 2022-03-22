# Adding Contents to Kiosk Endless Aisle

You can add update the content and configuration to a Kiosk Endless Aisle by clicking on the `Content` tab inside your installation.

> **Prerequisite:** Make sure you have integrated with [Grid Products](/apps/grid-products) before setting up the kiosk endless aisle to have populated data on the application.

### App Configurations
---
![](/assets/developer-access-token-timeout.png ":size=500")
- **Developer Access Token** (Required) - access token created from "Developers" tab (should have access to Space permission)
- **App Timeout in seconds** - time when screen is idle before the app resets the session and goes back to idle screen

![](/assets/mobile-transfer.png ":size=500")
- **Enable Mobile Session Transfer** - flag that allows the Kiosk Endless Aisle to transfer the session and shopping bag content to the configured Mobile Endless Aisle app *(you can identify which Mobile Endless Aisle a specific environment will redirect to)*

### Layout
---
![](/assets/layout-1.png ":size=500")
- **Logo** - logo to be displayed on the home screen of the application

#### Sticker Properties
- **Border Type** - type of sticker display <br/>
Options: 
  - **ROUNDED**: displayed on upper left of product card
  - **STRAIGHT**: displayed on bottom part of product card 

- **Sticker Display Type** - how sticker is presented in Product Info Page<br/>
Options: 
  - **Text Only**: displayed as text above the product name
  - **Beside Price**: displayed sticker beside the price label 

![](/assets/layout-2.png ":size=500")
- **Traditional Layout** <br/>
Options:
  - **Checked**: Logo is placed on home screen's top center followed by banners and categories
  ![](/assets/traditional.png ":size=300")
  - **Unchecked**: Logo is placed on home screen's header with option to place header label
  ![](/assets/non-traditional.png ":size=300")