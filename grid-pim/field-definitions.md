# Field Definitions
This document contains the definition of all fields mentioned in the Grid-PIM data-model document.

Nested structures are indicated by separate headers. 

| Field                  | Description                                                                                   | Required | Example            |
| ---------------------- | --------------------------------------------------------------------------------------------- | -------- | ------------------ |
| ProductId              | Primary ID of the product                                                                     | Yes      | product1           |
| Tenant                 | Name of client whom the data belongs                                                          | Yes      | Ombori             |
| Customers              | List of customers associated with the product                                                 |          | Ombori,IKEA        |
| IntroductionDate       | Date when product is available/added                                                          |          | 2012-05-05         |
| PlannedAbandonmentDate | Date when product is to be abandoned                                                          |          | 2030-05-05         |
| ShellLifeDays          |                                                                                               |          | 30                 |
| ProductType            | List of Product Type IDs applicable to this product as a reference from ProductTypes Database |          | ["item1", "item2"] |
### ProductName
ProductName is a **required** property that contains an Array of Objects, one is required, which each has the following properties

| Field         | Description                           | Required | Example                                              |
| ------------- | ------------------------------------- | -------- | ---------------------------------------------------- |
| ProductName   | Translation value of the product name | Yes      |                                                      |
| IsoLanguageId | Iso Language ID in BCP-47 format      | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId     | Country ID                            | Yes      | 46                                                   |

### ProductDescription
ProductDescription is a **required** property that contains an Array of Objects, one is required, which each has the following properties

| Field              | Description                                  | Required | Example                                              |
| ------------------ | -------------------------------------------- | -------- | ---------------------------------------------------- |
| ProductDescription | Translation value of the product description | Yes      |                                                      |
| IsoLanguageId      | Iso Language ID in BCP-47 format             | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId          | Country ID                                   | Yes      | 46                                                   |

### RelatedProducts
RelatedProducts is *not* required.

| Field              | Description                                  | Required | Example                                              |
| ------------------ | -------------------------------------------- | -------- | ---------------------------------------------------- |
| RelatedProductId | ID of the related product | Yes      |                                                      |
| ProductRelationshipType      | Relationship of the related product to the product             | Yes      | Recommended
   


### Variants
Variants is a **required** field

| Field                 | Description                                                                                                             | Required | Example                                                   |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------- | -------- | --------------------------------------------------------- |
| Id                    | Varient ID                                                                                                              | Yes      |                                                           |
| ProductId             | Product ID where variant belongs to                                                                                     | Yes      | product1                                                  |
| GlobalTradeItemNumber |                                                                                                                         |          |                                                           |
| GtinName              |                                                                                                                         |          |                                                           |
| EuropeanArticleNumber |                                                                                                                         |          |                                                           |
| UniversalProductCode  |                                                                                                                         |          |                                                           |
| PeriodStartDate       | Date when variant was added                                                                                             |          | 2021-01-01                                                |
| PeriodEndDate         | Date when variant will end                                                                                              |          | 2024-03-04                                                |
| ProductName           | The Name of the product variant, using the [ProductName](/grid-pim/field-definitions?id=productname) structure as above |          | [ProductName](/grid-pim/field-definitions?id=productname) |

### ProductStatus
ProductStatus is a **required** field.

| Field             | Description                                 | Required | Example                                              |
| ----------------- | ------------------------------------------- | -------- | ---------------------------------------------------- |
| ProductStatus     | Status value of the product                 | Yes      | `active` or `inactive`                               |
| CountryId         | Country ID where status is applicable       | Yes      | 46                                                   |
| IsoLanguageId     | Iso Language ID in BCP-47 format            | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| StoreId           | Store ID where product status is applicable |          |                                                      |
| PeriodStartDate   | Status duration start                       |          |                                                      |
| PeriodEndDate     | Status duration end                         |          |                                                      |
| ProductStatusNote |                                             |          |                                                      |

### ProductFeature
ProductFeature is *not* required.

| Field               | Description                             | Required | Example                                              |
| ------------------- | --------------------------------------- | -------- | ---------------------------------------------------- |
| Id                  | SKU or Variant ID                       | Yes      |                                                      |
| ProductFeatureType  | Key of the product feature              | Yes      |                                                      |
| ProductFeatureValue | Translated value of the product feature | Yes      |                                                      |
| IsoLanguageId       | Iso Language ID in BCP-47 format        | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId           | Country ID                              | Yes      | 46                                                   |

### ProductPriceList
ProductPriceList is a **required** field.

| Field                | Description                          | Required | Example                                                                                                              |
| -------------------- | ------------------------------------ | -------- | -------------------------------------------------------------------------------------------------------------------- |
| Id                   | SKU or Variant ID                    | Yes      |                                                                                                                      |
| PriceListType        | Standard or Promotional              | Yes      | Standard                                                                                                             |
| StoreId              | Store where price list is applicable |          |                                                                                                                      |
| IsoLanguageId        | Iso Language ID in BCP-47 format     | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids)                                                                 |
| CountryId            | Country ID                           | Yes      | 46                                                                                                                   |
| IsoCurrencyCode      | Iso Currency Code                    | Yes      | [IsoCurrencyCode List](https://docs.1010data.com/1010dataReferenceManual/DataTypesAndFormats/currencyUnitCodes.html) |
| PricingUomId         |                                      |          |                                                                                                                      |
| PeriodStartTimestamp | Price applicable start date          |          |                                                                                                                      |
| PeriodEndTimestamp   | Price applicable end date            |          |                                                                                                                      |
| SuggestedRetailPrice |                                      |          |                                                                                                                      |
| ListPrice            |                                      | Yes      |                                                                                                                      |

### CatalogPageLocationProduct

| Field                      | Description                            | Required | Example                                                       |
| -------------------------- | -------------------------------------- | -------- | ------------------------------------------------------------- |
| Id                         | SKU or Variant ID                      | Yes      |                                                               |
| ProductId                  | Parent ID                              | Yes      |                                                               |
| CatalogType                | Type of the image/media                |          | image/png<br>video/mp4                                        |
| CatalogPage                | Root URL where image/media is found    |          | [https://assets.example.com](/ ':disabled')                   |
| CatalogPageLocation        | ID or route where image/media is found |          | /images/image5.png                                            |
| CatalogPageLocationProduct | Entire URL where image/media is found  | Yes      | [https://assets.example.com/images/image5.png](/ ':disabled') |

### ProductLabel
ProductLabel is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field         | Description                            | Required | Example                                              |
| ------------- | -------------------------------------- | -------- | ---------------------------------------------------- |
| ProductLabel  | Translation value of the product label | Yes      |                                                      |
| IsoLanguageId | Iso Language ID in BCP-47 format       | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId     | Country ID                             | Yes      | 46                                                   |



### ProductItemQuantity
The inventory quantity

| Field                        | Description                                  | Required | Example |
| ---------------------------- | -------------------------------------------- | -------- | ------- |
| Id                           | SKU or Variant ID                            | Yes      |         |
| StoreId                      | Store where quantity/inventory is applicable |          |         |
| ProductItemQuantityStartDate | Quantity start date                          |          |         |
| ProductItemQuantityEndDate   | Quantity end date                            |          |         |
| ProductItemQuantity          | Product quantity value                       | Yes      |         |


### ProductShortDescription
ProductShortDescription is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field                   | Description                                        | Required | Example                                              |
| ----------------------- | -------------------------------------------------- | -------- | ---------------------------------------------------- |
| ProductShortDescription | Translation value of the short product description | Yes      |                                                      |
| IsoLanguageId           | Iso Language ID in BCP-47 format                   | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId               | Country ID                                         | Yes      | 46                                                   |


### ProductInternalName
ProductInternalName is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field               | Description                            | Required | Example                                              |
| ------------------- | -------------------------------------- | -------- | ---------------------------------------------------- |
| ProductInternalName | Translation of the internal name value | Yes      |                                                      |
| IsoLanguageId       | Iso Language ID in BCP-47 format       | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId           | Country ID                             | Yes      | 46                                                   |

### StorageInstructions
StorageInstructions is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field               | Description                             | Required | Example                                              |
| ------------------- | --------------------------------------- | -------- | ---------------------------------------------------- |
| StorageInstructions | Translation of the storage instructions | Yes      |                                                      |
| IsoLanguageId       | Iso Language ID in BCP-47 format        | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId           | Country ID                              | Yes      | 46                                                   |


### ConsumerStorageInstruction
ConsumerStorageInstruction is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field                      | Description                                              | Required | Example                                              |
| -------------------------- | -------------------------------------------------------- | -------- | ---------------------------------------------------- |
| ConsumerStorageInstruction | Translation of the storage instructions for the consumer | Yes      |                                                      |
| IsoLanguageId              | Iso Language ID in BCP-47 format                         | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId                  | Country ID                                               | Yes      | 46                                                   |


### ProductShippingInstruction
ProductShippingInstruction is *not* a required property that contains an Array of Objects, one is required, which each has the following properties.

| Field                      | Description                              | Required | Example                                              |
| -------------------------- | ---------------------------------------- | -------- | ---------------------------------------------------- |
| ProductShippingInstruction | Translation of the shipping instructions | Yes      |                                                      |
| IsoLanguageId              | Iso Language ID in BCP-47 format         | Yes      | [ISOLanguageID](/grid-pim/data-model?id=languageids) |
| CountryId                  | Country ID                               | Yes      | 46                                                   |
