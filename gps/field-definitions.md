# Field Definitions
This document contains the definition of all fields mentioned in the GPS data-model document.

Nested structures are indicated by separate headers. 

| Field | Description | Required | Example |
| ----- | ----------- | -------- | ------- |
|       |             |          |         |


| Field                  | Description                                   | Required | Example     |
| ---------------------- | --------------------------------------------- | -------- | ----------- |
| ProductId              | Primary ID of the product                     | Yes      | product1    |
| Tenant                 | Name of client whom the data belongs          | Yes      | Ombori      |
| Customers              | List of customers associated with the product |          | Ombori,IKEA |
| IntroductionDate       | Date when product is available/added          |          | 2012-05-05  |
| PlannedAbandonmentDate | Date when product is to be abandoned          |          | 2030-05-05  |
| ShellLifeDays          |                                               |          | 30          |

### ProductName
ProductName is a **required** property which contains an Array of Objects, one is required, which each has the following properties

| Field         | Description                           | Required | Example                                         |
| ------------- | ------------------------------------- | -------- | ----------------------------------------------- |
| ProductName   | Translation value of the product name | Yes      |                                                 |
| IsoLanguageId | Iso Language ID in BCP-47 format      | Yes      | [ISOLanguageID](/gps/data-model?id=languageids) |
| CountryId     | Country ID                            | Yes      | 46                                              |

### ProductDescription
ProductDescription is a **required** property which contains an Array of Objects, one is required, which each has the following properties

| Field              | Description                                  | Required | Example                                         |
| ------------------ | -------------------------------------------- | -------- | ----------------------------------------------- |
| ProductDescription | Translation value of the product description | Yes      |                                                 |
| IsoLanguageId      | Iso Language ID in BCP-47 format             | Yes      | [ISOLanguageID](/gps/data-model?id=languageids) |
| CountryId          | Country ID                                   | Yes      | 46                                              |

### Variants
Varients is a **required** field

| Field                 | Description                                                                                                       | Required | Example                                             |
| --------------------- | ----------------------------------------------------------------------------------------------------------------- | -------- | --------------------------------------------------- |
| Id                    | Varient ID                                                                                                        | Yes      |                                                     |
| ProductId             | Product ID where variant belongs to                                                                               | Yes      | product1                                            |
| GlobalTradeItemNumber |                                                                                                                   |          |                                                     |
| GtinName              |                                                                                                                   |          |                                                     |
| EuropeanArticleNumber |                                                                                                                   |          |                                                     |
| UniversalProductCode  |                                                                                                                   |          |                                                     |
| PeriodStartDate       | Date when variant was added                                                                                       |          | 2021-01-01                                          |
| PeriodEndDate         | Date when variant will end                                                                                        |          | 2024-03-04                                          |
| ProductName           | The Name of the product variant, using the [ProductName](gps/field-definitions?id=productname) structure as above |          | [ProductName](gps/field-definitions?id=productname) |

### ProductStatus
ProductStatus is a **required** field.

| Field             | Description                                 | Required | Example                                         |
| ----------------- | ------------------------------------------- | -------- | ----------------------------------------------- |
| ProductStatus     | Status value of the product                 | Yes      | `active` or `inactive`                          |
| CountryId         | Country ID where status is applicable       | Yes      | 46                                              |
| IsoLanguageId     | Iso Language ID in BCP-47 format            | Yes      | [ISOLanguageID](/gps/data-model?id=languageids) |
| StoreId           | Store ID where product status is applicable |          |                                                 |
| PeriodStartDate   | Status duration start                       |          |                                                 |
| PeriodEndDate     | Status duration end                         |          |                                                 |
| ProductStatusNote |                                             |          |                                                 |

### ProductFeature
ProductFeature is *not* required.

| Field               | Description                             | Required | Example                                         |
| ------------------- | --------------------------------------- | -------- | ----------------------------------------------- |
| Id                  | SKU or Variant ID                       | Yes      |                                                 |
| ProductFeatureType  | Key of the product feature              | Yes      |                                                 |
| ProductFeatureValue | Translated value of the product feature | Yes      |                                                 |
| IsoLanguageId       | Iso Language ID in BCP-47 format        | Yes      | [ISOLanguageID](/gps/data-model?id=languageids) |
| CountryId           | Country ID                              | Yes      | 46                                              |

### ProductPriceList
ProductPriceList is a **required** field.

| Field                | Description                          | Required | Example                                                                                                              |
| -------------------- | ------------------------------------ | -------- | -------------------------------------------------------------------------------------------------------------------- |
| Id                   | SKU or Variant ID                    | Yes      |                                                                                                                      |
| PriceListType        | Standard or Promotional              | Yes      | Standard                                                                                                             |
| StoreId              | Store where price list is applicable |          |                                                                                                                      |
| IsoLanguageId        | Iso Language ID in BCP-47 format     | Yes      | [ISOLanguageID](/gps/data-model?id=languageids)                                                                      |
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
