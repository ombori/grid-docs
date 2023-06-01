# Grid Product Release Notes
Grid Product receives continuous updates. All the recent release notes can be found below in order of release. 
s
## 2023-06-01
- Search endpoint fix for product types

## 2023-05-11
- Search endpoint logic fix

## 2023-05-10
- Improved products list endpoint (v2)

## 2023-05-05
- Product type endpoint to return results with products only

## 2023-04-20
- Remove leading zeros for barcode related fields (europeanArticleNumber, universalProductCode, globalTradeItemNumber)

## 2023-04-19
- Improved product by barcode endpoint

## 2023-02-23
- Fixes on product push operations (image processing)

## 2023-01-26
- Fix upload products by excel endpoint

## 2023-01-25
- Product by barcode lookup with raw value and one leading 0

## 2023-01-12
- Price list type extension

## 2022-10-25
- Update base URL endpoints to https://api.omborigrid.com/regions/{data-residency}/products/v1/tenants

## 2022-03-22

### Features
- [Product Variant](/grid-products/api?id=get-product-variant) Endpoint

### Model
- Added [VariantInfo](/grid-products/data-model?id=variantinfo) type

## 2022-03-07

### Features
- Add `count` on [Products API](/grid-products/api?id=get-post-products) response
- Add `includeProductsByVariantsByGroupId` flag on [Product API](/grid-products/api?id=get-product-by-id) and [Product-Barcode API](/grid-products/api?id=get-product-by-barcode) request parameter

### Grid Product Model
- Add `variantsGroupId` field
- Add `colorImageUrl` on `variants` field

## 2022-01-20

#### Features
- [Update Variants](/grid-products/api?id=patch-update-variants) Endpoint

#### Model
- Added [VariantUpdateFields](/grid-products/data-model?id=variantupdatefields) type

## 2022-01-18

#### Model Updates
Renamed the ff. fields:
- `productId` => `productGroupId`
- variants.`id` => variants.`productId`
- variants.`productId` => variants.`productGroupId`
- `relatedProducts` => `relatedProductGroups`
- `relatedProducts.relatedProductId` => `relatedProductGroups.relatedProductGroupId`
- productFeature.`id` => productFeature.`productId`
- productPriceList.`id` => productPriceList.`productId`
- catalogPageLocationProduct.`id` => catalogPageLocationProduct.`productId`
- catalogPageLocationProduct.`productId` => catalogPageLocationProduct.`productGroupId`
- productItemQuantity.`id` => productItemQuantity.`productId`

## 2022-01-17

#### Model Updates
- Added `spaceId` on `productLabel` fields
- Fixed links

## 2022-01-04

#### Integration Flow
- Introduced Spaces which are used to identify to which space-specific data => visible (if set)
- Added Spaces integration and use the generated `spaceId` on the GridProduct model (if applicable)

#### Model Updates
- Updated field names from PascalCase to camelCase
- Removed Customers field
- Removed `CountryId` fields
- Added `spaceIds` field (contains list of spaceIds where the product => visible. Visible to all if empty array)
- Changed `StoreId` fields to `spaceId` (identifier where data is applicable. Visible to all if unset)
   - `spaceId` are generated from Spaces API Endpoints
- Change `spaceId` to a mandatory fields
- Change `spaceIds` to a mandatory field
- Changed `variants.globalTradeItemNumber` type to `Array<string>`
- Changed `variants.gtinName` type to `Array<string>`
- Changed `variants.europeanArticleNumber` type to `Array<string>`
- Changed `variants.universalProductCode` type to `Array<string>`
- Set `relatedProducts.productRelationshipType` type to `ProductRelationshipTypes`
- Added `ProductRelationshipTypes` enum definition

#### API Updates
- Updated available API endpoints per data residency (`EU`, `US`, `UAE`, `IN`, `AU`)

#### Features
- Get Product Recommendations by ID