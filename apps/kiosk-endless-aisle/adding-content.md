# Adding Contents to Kiosk Endless Aisle

You can add update the content and configuration to a Kiosk Endless Aisle by clicking on the `Content` tab inside your installation.

> **Prerequisite:** Make sure you have integrated with [Grid Products](/apps/grid-products) before setting up the kiosk endless aisle to have populated data on the application.

### App Configurations
---
![](/assets/developer-access-token-timeout.png ":size=500")
- **App Timeout in seconds** - time when screen is idle before the app resets the session and goes back to idle screen

![](/assets/mobile-transfer.png ":size=500")
- **Enable Mobile Session Transfer** - flag that allows the Kiosk Endless Aisle to transfer the session and shopping bag content to the configured Mobile Endless Aisle app *(you can identify which Mobile Endless Aisle a specific environment will redirect to)*

### Layout
---
![](/assets/layout-1.png ":size=500")
- **Logo** - logo to be displayed on the home screen of the application

#### Sticker Properties
- **Border Type** - type of sticker display 
  - **ROUNDED**: displayed on upper left of product card
  - **STRAIGHT**: displayed on bottom part of product card 

- **Sticker Display Type** - how sticker is presented in Product Info Page
  - **Text Only**: displayed as text above the product name
  - **Beside Price**: displayed sticker beside the price label 

![](/assets/layout-2.png ":size=500")
- **Traditional Layout**
  - **Checked**: Logo is placed on home screen's top center followed by banners and categories

  ![](/assets/traditional.png ":size=300")
  - **Unchecked**: Logo is placed on home screen's header with option to place header label
 
  ![](/assets/non-traditional.png ":size=300")

- **Product Gallery Orientation**
  - **LANDSCAPE**<br/>
  ![](/assets/gallery-landscape.png ":size=300")
  - **PORTRAIT**<br/>
  ![](/assets/gallery-portrait.png ":size=300")
  
- **Product Description Placement**
  - **SLIDE-OUT** - display description sliding out from the left with a click of a button
  - **BUILT-IN** - display description within the container (toggable)

- **Prices alignment** - price alignment on product listing and product info page

- **Omnibar Layout**
  - **ROUNDED** - with border radius display
  - **STRAIGHT** - with straigth borders

### Features
---
![](/assets/feature-1.png ":size=300")
![](/assets/feature-2.png ":size=300")
- **Move Categories to Explore screen**
  - **Checked** - new "Explore" button in the Omnibar appears that redirects to a page with the configured categories
  - **Unchecked** - Configured categories are displayed on Home Screen below the configured banners

#### Help
- **Call for help** - displays "Help" button in omnibar that calls an external API to inform that help is needed on the kiosk. Request parameters, headers, and modal labels are configurable. 

![](/assets/feature-3.png ":size=300")

#### Shopping Bag
- **Show Bag Button** - enables shopping bag / cart features
  - **ENABLED**:
    - **Display Total Discount Calculation** - displays "Discount" row and value in order summary
    - **Type of Notification (when product is added to bag)**
       - **TOAST** - displays notification on header area<br/>
       ![](/assets/notif-toast.png ":size=300")
       - **OMNIBAR** - displays animation on omnibar<br/>
       ![](/assets/notif-omnibar.png ":size=300")

    - **Checkout Method**
       - **External** - enables handover of items to external URL by passing shopping bag content as parameters. Modal labels, and additional parameters could be configured.
       - **Print Barcode** - integrate with thermal printer to print out shopping bag info on receipt with corresponding barcode values.
       - **Print Barcode with Customer Info, and Queue** - same with Print Barcode, but allows user to input user information on screen, and integrates with Task App.

#### Filter
![](/assets/feature-7.png ":size=500")
- **Filter** - enables showing of filter options in product listing page<br/>
    - **Filter Option Keys**
        - **Label** - label to be displayed on filter option on screen
        - **Key** - productFeature[].productFeatureType field where option is extracted from Grid Products

#### Others
![](/assets/feature-8.png ":size=500")
- **Inventory availability check**<br/>
    - **Checked** - add to shopping bag will be displayed if product inventory is out of stock
    - **Unchecked** - product can be added to shopping bag regardless of inventory count

- **Display suggested retail price**<br/>  
    - **Checked** - the product's "Standard" suggestedListPrice will be displayed as slashed out price if it's lesser than the listPrice value ("Promotional" price display logic applies)
    - **Unchecked** - only the product's "Standard" listPrice will be displayed by default ("Promotional" price display logic applies)
<br/>

### Idle
---
![](/assets/idle.png ":size=500")
- **Display options**<br/>
    - **DEFAULT** - divides screen into half. Left side contains image/video media, right side contains primary color with CTA button
    - **CUSTOM** - displays Home screen as overlay, and blinks when kiosk detects motion and face.

- **Splash Media** - the image/video to be displayed on screen (for Default display option)

- **CTA label** - configurable Call to action button label

- **Button Theme** - color of the Call to action button based on theme

### Product Page
---
![](/assets/product-page.png ":size=500")
- **Display stock** - display product's available stock
![](/assets/in-stock.png ":size=500")

#### Recommendations
- **Scroll Direction**
    - **Vertical** - displays product recommendations in a 3 column grid
    - **Horizontal** - displays product recommendations in a single row that's scrollable horizontally
- **Source**
    - **Default** - data taken from Grid Products directly (`relatedProductGroups` field)
    - **Streamoid** - data taken from Streamoid service. Needs streamoid refresh token.

### Banners
![](/assets/banner-1.png ":size=500")<br/>
- **Title** - banner title on large font

- **Description** - label displayed on smaller font size

- **CTA** - label for the call to action button<br/>

- **Type** - either image or video media. Click on `Pick an asset` to upload and choose the media to display

#### Styles and On Click
![](/assets/banner-2.png ":size=500")
- Default banner display<br/>
![](/assets/banner-default.png ":size=300")

- **Styles** - overrides CSS styling for the banner element (Banners container make use of [Grid layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout))

- **On click**
    - **CLICK_PRODUCT** - redirects to product info page. Need to specify `productGroupId` from Grid Products
    - **CLICK_CATEGORY** - redirects to product listing page for selected category. Need to specify `productTypeId` from Grid Products [product types](http://localhost:3000/#/grid-products/data-model?id=producttype) data
    - **NONE** - no action


### Categories
![](/assets/category.png ":size=500")<br/>

- **ID** - specify the `productTypeId` from Grid Products [product types](http://localhost:3000/#/grid-products/data-model?id=producttype) data. On category click, redirects to the product listing page for the configured category.

- **Title** - label to be displayed on the tile

- **Type** - either image or video media. Click on `Pick an asset` to upload and choose the media to display

- Default category display<br/>
![](/assets/category-default.png ":size=300")

- **Styles** - overrides CSS styling for the category element (Categories container make use of [Grid layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout))


### Fonts
![](/assets/fonts.png ":size=500")
- Set font files for light, regular, and bold font weights.
- Click on `Pick an asset` to upload and choose a valid font file for app to use

### Product Card Style
![](/assets/product-card-style.png ":size=500")
- Allows overriding the CSS styles of different elements of the product card displayed on product listing page
- Default product card display<br/>
![](/assets/product-card-default.png ":size=300")

### Theme
![](/assets/theme-1.png ":size=500")
![](/assets/theme-2.png ":size=500")
- **Theme style** - either `LIGHT` or `DARK` which inverts the text colors based on configured theme colors.

- **Buttons border type**
    - **ROUNDED** - all button elements will have rounded corners
    - **STRAIGHT** - all button elements will have sharp/straight corners

- #### Colors
    - **Primary** - used on buttons, headers, stickers, active buttons
    - **Secondary** - used on buttons, notifications, loading indicators
    - **Danger**
    - **Light** - used on texts, buttons
    - **Dark** - used on texts, buttons
    - **Promo** - used on promotional price label
    - **Border** - user on border styles
    - **Omnibar and Keyboard Background** - used in omnibar and keyboard
    - **Main Screen Background** - used as default background color and most parts of the app
    - **Secondary Screen Background** - used as background color on most parts of the app
    - **Background for variant selector** - used on variant selector (inactive)

- #### Shadows
    - Configuration for shadow css styling in app


## Publishing to device
Now that you have updated the content and configuration of your app, you can publish a build to your Kiosk Endless Aisle device. If you don't have a device attached to your installation, do so now. 

?> To learn more about how to add a device to the Ombori grid, visit the [Add a device](/general/adding-device.md) documentation.

?> Also please take note of the [Additional device setup instructions](/apps/kiosk-endless-aisle/setting-up.md?id=device-setup-instructions)

`Save all changes` button appears when you do any update on the content tab.
![](/assets/save-changes.png ":size=400 :no-zoom")

After you've pressed `Save all changes` a new button appears, this is the `Publish` button.

![](/assets/publish-prod.png ":size=400 :no-zoom")

Once you press `Publish` button, the Kiosk Endless Aisle application will start building, and then will be automatically downloaded to the devices added to the installation having `Prod` environment settings. 

![](/assets/publish-others.png ":size=400 :no-zoom")

You can also deploy your application to other environments (other than `Prod`) after saving changes. Click on the 3 dots button beside "Publish" and choose what environment you want to deploy, it will then be automatically downloaded to the devices having the specified environment settings.

You will notice on the screen of your device a progress bar will display notifying you of it downloading the assets, and then it will start showing the content you've configured.
