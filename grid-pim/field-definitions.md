# Field Definitions
This document contains the definition of all fields mentioned in the Grid-PIM data-model document.

Nested structures are indicated by separate headers. 

| Field                  | Description                                                                                   | Required | Example            |
| ---------------------- | --------------------------------------------------------------------------------------------- | -------- | ------------------ |
| productId              | Primary ID of the product                                                                     | Yes      | product1           |
| spaces              | List of spaceIds where product will be visible                                                |          | `<ombori generated spaceId>`        |
| introductionDate       | Date when product is available/added                                                          |          | 2012-05-05         |
| plannedAbandonmentDate | Date when product is to be abandoned                                                          |          | 2030-05-05         |
| shellLifeDays          |                                                                                               |          | 30                 |
| productType            | List of Product Type IDs applicable to this product as a reference from ProductTypes Database |          | ["furniture", "outdoor"] |
### productName
productName is a **required** property that contains an Array of Objects, one is required, which each has the following properties

| Field         | Description                           | Required | Example                                              |
| ------------- | ------------------------------------- | -------- | ---------------------------------------------------- |
| productName   | Translation value of the product name | Yes      |                                                      |
| isoLanguageId | Iso Language ID in BCP-47 format      | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |


### productDescription
productDescription is a **required** property that contains an Array of Objects, one is required, which each has the following properties

| Field              | Description                                  | Required | Example                                              |
| ------------------ | -------------------------------------------- | -------- | ---------------------------------------------------- |
| productDescription | Translation value of the product description | Yes      |                                                      |
| isoLanguageId      | Iso Language ID in BCP-47 format             | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |

### relatedProducts
relatedProducts is *not* required.

| Field                   | Description                                        | Required | Example     |
| ----------------------- | -------------------------------------------------- | -------- | ----------- |
| relatedProductId        | ID of the related product                          | Yes      |             |
| productRelationshipType | Relationship of the related product to the product | Yes      | Recommended |
   


### variants
variants is a **required** field

| Field                 | Description                                                                                                             | Required | Example                                                   |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------- | -------- | --------------------------------------------------------- |
| id                    | Variant ID                                                                                                              | Yes      |                                                           |
| productId             | Product ID where variant belongs to                                                                                     | Yes      | product1                                                  |
| globalTradeItemNumber | Array of variant's Global Trade Item Number                                                                                                                         |          | []                                                          |
| gtinName              |   Array of variant's Gtin Name                                                                                                                       |          |                                                           []|
| europeanArticleNumber |Array of variant's European Article Number                                                                                                                         |          |[]                                                           |
| universalProductCode  | Array of variant's Universal Product Code                                                                                                                                           |          |                                                     []      |
| periodStartDate       | Date when variant was added                                                                                             |          | 2021-01-01                                                |
| periodEndDate         | Date when variant will end                                                                                              |          | 2024-03-04                                                |
| productName           | The Name of the product variant, using the [productName](/grid-pim/field-definitions?id=productname) structure as above |          | [productName](/grid-pim/field-definitions?id=productname) |

### productStatus
productStatus is a **required** field.

| Field             | Description                                 | Required | Example                                              |
| ----------------- | ------------------------------------------- | -------- | ---------------------------------------------------- |
| productStatus     | Status value of the product                 | Yes      | `active` or `inactive`                               |
| isoLanguageId     | Iso Language ID in BCP-47 format            | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| spaceId           | Store ID where product status is applicable |          |                                                      |
| periodStartDate   | Status duration start                       |          |                                                      |
| periodEndDate     | Status duration end                         |          |                                                      |
| productStatusNote |                                             |          |                                                      |

### productFeature
productFeature is *not* required.

| Field               | Description                             | Required | Example                                              |
| ------------------- | --------------------------------------- | -------- | ---------------------------------------------------- |
| id                  | Variant ID                       | Yes      |                                                      |
| productFeatureType  | Key of the product feature              | Yes      |                                                      |
| productFeatureValue | Translated value of the product feature | Yes      |                                                      |
| isoLanguageId       | Iso Language ID in BCP-47 format        | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |

### productPriceList
productPriceList is a **required** field.

| Field                | Description                          | Required | Example                                                                                                              |
| -------------------- | ------------------------------------ | -------- | -------------------------------------------------------------------------------------------------------------------- |
| id                   | Variant ID                    | Yes      |                                                                                                                      |
| priceListType        | Standard or Promotional              | Yes      | Standard                                                                                                             |
| spaceId              | Space where price list is applicable |          |                                                                                                                      |
| isoLanguageId        | Iso Language ID in BCP-47 format     | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids)                                                                 |
| isoCurrencyCode      | Iso Currency Code                    | Yes      | [IsoCurrencyCode List](https://docs.1010data.com/1010dataReferenceManual/DataTypesAndFormats/currencyUnitCodes.html) |
| pricingUomId         |                                      |          |                                                                                                                      |
| periodStartTimestamp | Price applicable start date          |          |                                                                                                                      |
| periodEndTimestamp   | Price applicable end date            |          |                                                                                                                      |
| suggestedRetailPrice |                                      |          |                                                                                                                      |
| listPrice            |                                      | Yes      |                                                                                                                      |

### catalogPageLocationProduct

| Field                      | Description                            | Required | Example                                                       |
| -------------------------- | -------------------------------------- | -------- | ------------------------------------------------------------- |
| id                         | Variant ID                      | Yes      |                                                               |
| productId                  | Parent ID                              | Yes      |                                                               |
| catalogType                | Type of the image/media                |          | image/png<br>video/mp4                                        |
| catalogPage                | Root URL where image/media is found    |          | [https://assets.example.com](/ ':disabled')                   |
| catalogPageLocation        | ID or route where image/media is found |          | /images/image5.png                                            |
| catalogPageLocationProduct | Entire URL where image/media is found  | Yes      | [https://assets.example.com/images/image5.png](/ ':disabled') |

### productLabel
productLabel is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field         | Description                            | Required | Example                                              |
| ------------- | -------------------------------------- | -------- | ---------------------------------------------------- |
| productLabel  | Translation value of the product label | Yes      |                                                      |
| isoLanguageId | Iso Language ID in BCP-47 format       | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |


### productTags
productTags is *not* a required property that contains an Array of Objects, one is required, which each has the following properties. This field could help in the searchability of a product.

| Field         | Description                             | Required | Example                                              |
| ------------- | --------------------------------------- | -------- | ---------------------------------------------------- |
| productTags   | Array of translated strings of the tags | Yes      |                                                      |
| isoLanguageId | Iso Language ID in BCP-47 format        | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |



### productItemQuantity
The inventory quantity

| Field                        | Description                                  | Required | Example |
| ---------------------------- | -------------------------------------------- | -------- | ------- |
| id                           | Variant ID                            | Yes      |         |
| spaceId                      | Space where quantity/inventory is applicable |          |         |
| productItemQuantityStartDate | Quantity start date                          |          |         |
| productItemQuantityEndDate   | Quantity end date                            |          |         |
| productItemQuantity          | Product quantity value                       | Yes      |         |


### productShortDescription
productShortDescription is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field                   | Description                                        | Required | Example                                              |
| ----------------------- | -------------------------------------------------- | -------- | ---------------------------------------------------- |
| productShortDescription | Translation value of the short product description | Yes      |                                                      |
| isoLanguageId           | Iso Language ID in BCP-47 format                   | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |


### productInternalName
productInternalName is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field               | Description                            | Required | Example                                              |
| ------------------- | -------------------------------------- | -------- | ---------------------------------------------------- |
| productInternalName | Translation of the internal name value | Yes      |                                                      |
| isoLanguageId       | Iso Language ID in BCP-47 format       | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |

### storageInstructions
storageInstructions is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field               | Description                             | Required | Example                                              |
| ------------------- | --------------------------------------- | -------- | ---------------------------------------------------- |
| storageInstructions | Translation of the storage instructions | Yes      |                                                      |
| isoLanguageId       | Iso Language ID in BCP-47 format        | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |


### consumerStorageInstruction
consumerStorageInstruction is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field                      | Description                                              | Required | Example                                              |
| -------------------------- | -------------------------------------------------------- | -------- | ---------------------------------------------------- |
| ConsumerStorageInstruction | Translation of the storage instructions for the consumer | Yes      |                                                      |
| isoLanguageId              | Iso Language ID in BCP-47 format                         | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |


### productShippingInstruction
productShippingInstruction is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field                      | Description                              | Required | Example                                              |
| -------------------------- | ---------------------------------------- | -------- | ---------------------------------------------------- |
| productShippingInstruction | Translation of the shipping instructions | Yes      |                                                      |
| isoLanguageId              | Iso Language ID in BCP-47 format         | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
