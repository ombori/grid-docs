# Adding Contents to Smart Fitting Room

You can add update the content and configuration to a Smart Fitting Room by clicking on the `Content` tab inside your installation.

> **Prerequisite:** Make sure you have integrated with [Grid Products](/apps/grid-products) before setting up the smart fitting room to have populated data on the application.

---
![](/assets/sfr-setting-1.png ":size=500")
### Enable NPS
  - Toggles the capturing of user feedback (NPS) along the journey in Smart Fitting Room

### Queue settings
 > Note: This is just a temporary setting format, so in near future setting up this field will be simpler
  
  ![](/assets/sfr-setting-1.png ":size=700")

  - **<ins>Queue API url</ins>**   
    - Value can be formatted using `{baseUrl}/api/organizations/{tasksAppManagerUrl}`
      - `baseUrl` depends on data residency of the tenant
        - **EU**: https://ombori-queue-prod-eu.azure-api.net
        - **US**: https://ombori-queue-prod-us.azure-api.net
        - **UAE**: https://ombori-queue-prod-uae.azure-api.net
        - **AU**: https://ombori-queue-prod-au.azure-api.net
        - **IN**: https://queue-prod-in.omborigrid.com/
      ---

      ![](/assets/sfr-queue-api.png ":size=500")
      - `tasksAppManagerUrl`can be found when you open the [Tasks App Manager](/#/apps/tasks-app/setting-up?id=general-settings:~:text=the%20Tasks%20Manager-,Tasks%20manager%20link,-Quick%20access%20link) link from the Tasks App installation (#7)
        - Take the value after the "omborigrid.com/" and before "/admin" from the URL
        - Example: `ombori-tenant/queues/XXXX-XXXX-XXXX`)

  - **<ins>Space Name</ins>**
    > You can provide any value here for now. Will be deprecated and not in use already.   

### Timeouts
  ![](/assets/sfr-timeouts.png ":size=700")
  - **<ins>App Timeout in seconds</ins>**
    - Duration that screen is idle without any interactions before it prompts the confirmation if customer is still in the room
      - If no response, it redirects the app back to Idle screen
  - **<ins>Timeout to auto-cancel "bring to me" request items (in seconds)</ins>**
    - Duration before a newly added request in Tasks App is automatically canceled if no update (moving ticket to "Preparing") was done on the ticket

---

![](/assets/sfr-coverage-disabled.png ":size=700")

### Product Types coverage (Optional)
  - List of product type IDs that are filtered out to be displayed on the solution (all children of specified productTypeId will be automatically covered)

### Disabled Product Types request (Optional)
  - List of product type IDs where request to be bought to the fitting room is disabled

---

![](/assets/sfr-layout.png ":size=700")

### Layout
  - **Product gallery orientation**
    - **LANDSCAPE**<br/>
    ![](/assets/gallery-landscape.png ":size=300")
    - **PORTRAIT**<br/>
    ![](/assets/gallery-portrait.png ":size=300")

  - **Product Description Placement**
    - **SLIDE-OUT** - display description sliding out from the left with a click of a button
    - **BUILT-IN** - display description within the container (toggable)

  - **Prices alignment** - price alignment on product listing and product info page

---

### Features
![](/assets/sfr-features.png ":size=700")

  - **Manual End Session**
  
    ![](/assets/sfr-end-session.png ":size=500")

    - Shows the "End Session" button in the sidebar which allows the user to manually end the session any part of the journey
    - If disabled, session will only end when screen is idle after App Timeout (in seconds)
  
  - **Clear tickets on idle timeout**
    - Clears/cancels all the requested items to the Tasks App in the current session once smart fitting room app times out
  
  - **Inventory availability check**
    - If enabled, item can't be requested if there's no item quantity for the variant in Grid Products

  - **Display suggested retail price**
    - Option to show suggested retail price along with the active list price (shown as slashed price if active list price is lower than SRP)
  
  - **Use suggested retail price as base price**
    - Option to make the suggested retail price as the base price
    - If enabled, the promotional price check will be based on the SRP and not the active list price

  - **Display waiting time based on inventory location**
    - Adds an external inventory and location validation check to indicate if item is available and display estimated waiting time
    - **Note**: This requires direct integration with Grid Products to enable this feature

      - **Request Device ID**
        - Hardcoded device ID to be called when requesting the integrated API call

      - **Message to display when product is not available**
      
      - **Message to display when inventory API returns unexpected error**
      
      - **Front office waiting time label**
        - Message to display if any item is available in FOH
      
      - **Enable request for items found on back office only**
        - By default, items that are only found in front office (FOH) can be requested
        - If enabled, this will allow items that are only available in back office (BOH) be requested

---

### Idle

---
![](/assets/sfr-idle.png ":size=700")

- **Splash Media** - the image/video to be displayed on screen (for Default display option)

### Product Card Style
![](/assets/sfr-product-card-style.png ":size=500")
- Allows overriding the CSS styles of different elements of the product card displayed on product listing page
- Default product card display<br/>
![](/assets/product-card-default.png ":size=300")

### Active - Product Page
![](/assets/sfr-labels.png ":size=700")
  - **Try more options label**
  - **Try more options description**
  - **Bring to me label**
---
![](/assets/sfr-active-product.png ":size=700")

  - **Display stocks**
    - Display product variant's available stock in PDP
  
  - **Recommendations**
    - **Scroll Direction**
      - **Vertical** - displays product recommendations in a 3 column grid
      - **Horizontal** - displays product recommendations in a single row that's scrollable horizontally

  - **Source**
      - **Default** - data taken from Grid Products directly (`relatedProductGroups` field)
      - **Streamoid** - data taken from Streamoid service. Needs streamoid refresh token.

### Requested Item Modal
  - Modal displayed when clicking the requested items being prepared in the sidebar

  ![](/assets/sfr-modal-view.png ":size=500")

  - **Item For Preparation** - labels if item is still under "For preparation" column in Tasks App
  
  - **Item being Prepared** - labels if item is under "Preparing" column in Tasks App
  
  - **Item Cancelled (Out of Stock)** - labels if item was cancelled by Staff in Tasks App due to being out of stock

  - **Item Cancelled (Staff is Unavailable)** - labels if item was auto-cancelled because no staff is able to acknowledge preparation of the item after the configured *Timeout to auto-cancel "bring to me" request items (in seconds)*

  - **Item Delivered** - labels if item was marked as Delivered in Tasks App


### Fonts
![](/assets/fonts.png ":size=500")
- Set font files for light, regular, and bold font weights.
- Click on `Pick an asset` to upload and choose a valid font file for app to use

### Theme
![](/assets/sfr-theme.png ":size=500")
- **Theme style** - either `LIGHT` or `DARK` which inverts the text colors based on configured theme colors.

- **Buttons border type**
    - **ROUNDED** - all button elements will have rounded corners
    - **STRAIGHT** - all button elements will have sharp/straight corners

- #### Colors
  - **Primary** - used on buttons, stickers, active buttons
  - **Secondary** - used on buttons, notifications, loading indicators
  - **Danger** - used on buttons, notifications
  - **Light** - used on texts, buttons
  - **Dark** - used on texts, buttons
  - **Promo** - used on promotional price label
  - **Border** - user on border styles
  - **Main Screen Background** - used as default background color and most parts of the app
  - **Secondary Screen Background** - used as background color on most parts of the app
  - **Background for variant selector** - used on variant selector (inactive)
  - **Sidebar** - used as background color of left sidebar

- #### Shadows
  - Configuration for shadow css styling in app

## Publishing to device
Now that you have updated the content and configuration of your app, you can publish a build to your Smart Fitting Room device. If you don't have a device attached to your installation, do so now. 

?> To learn more about how to add a device to the Ombori grid, visit the [Add a device](/general/adding-device.md) documentation.

?> Also please take note of the [Additional device setup instructions](/apps/smart-fitting-room/setting-up.md?id=device-setup-instructions)

`Save all changes` button appears when you do any update on the content tab.
![](/assets/save-changes.png ":size=400 :no-zoom")

After you've pressed `Save all changes` a new button appears, this is the `Publish` button.

![](/assets/publish-prod.png ":size=400 :no-zoom")

Once you press `Publish` button, the Kiosk Endless Aisle application will start building, and then will be automatically downloaded to the devices added to the installation having `Prod` environment settings. 

![](/assets/publish-others.png ":size=400 :no-zoom")

You can also deploy your application to other environments (other than `Prod`) after saving changes. Click on the 3 dots button beside "Publish" and choose what environment you want to deploy, it will then be automatically downloaded to the devices having the specified environment settings.

You will notice on the screen of your device a progress bar will display notifying you of it downloading the assets, and then it will start showing the content you've configured.

## Setup RFID Reader
After publishing the application, you'll be required to setup any of our supported RFID readers which will be used to detect the garments placed in the Fitting Room.

?> To learn more about how to add a RFID Reader, visit the [RFID Reader Setup](/apps/rfid-reader/) documentation.