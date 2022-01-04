# Grid PIM Release Notes
The Grid PIM receives continuous updates. All the recent release notes can be found below in order of release. 

## 2021-01-04

#### Integration Flow
- Introduced Spaces which will be used to identify to which space a specific data will be visible (if set)
- Added Spaces integration, and use the generated spaceId on the GridProduct model (if applicable)

#### Model Updates
- Updated field names from PascalCase to camelCase
- Removed Customers field
- Removed CountryId fields
- Added spaceIds field (contains list of spaceIds where the product will be visible. Visible to all if empty array)
- Changed StoreId fields to spaceId (identifier where data is applicable. Visible to all if unset)
   - spaceId are generated from Spaces API Endpoints
- Change spaceId as mandatory fields
- Change spaceIds as mandatory field
- Changed variants.globalTradeItemNumber type to `Array<string>`
- Changed variants.gtinName type to `Array<string>`
- Changed variants.europeanArticleNumber type to `Array<string>`
- Changed variants.universalProductCode type to `Array<string>`
- Set relatedProducts.productRelationshipType type to `ProductRelationshipTypes`
- Added ProductRelationshipTypes enum definition

### API Updates
- Updated available API endpoints per data residency (eu, us, uae, in, au)

#### Features
- Get Product Recommendations by ID