# Grid Product Release Notes
Grid Product receives continuous updates. All the recent release notes can be found below in order of release. 

## 2021-01-17

#### Model Updates
- Added `spaceId` on `productLabel` fields
- Fixed links

## 2021-01-04

#### Integration Flow
- Introduced Spaces which are used to identify to which space-specific data will be visible (if set)
- Added Spaces integration and use the generated `spaceId` on the GridProduct model (if applicable)

#### Model Updates
- Updated field names from PascalCase to camelCase
- Removed Customers field
- Removed `CountryId` fields
- Added `spaceIds` field (contains list of spaceIds where the product will be visible. Visible to all if empty array)
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