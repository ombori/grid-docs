# Grid Products API Reference

This is the API reference for Grid Products integration. 

## Postman Collection
For easy configuration and testing, here's a Postman collection you can import into Postman.

?> Download the [Postman Collection](https://www.getpostman.com/collections/60c91683eadfae325b83)

- URL: 
  - Please change the values for `<tenant-id>`, `<environment>`, and `<space-id>`
  - Please change the value of `<data-residency>` with either `eu`, `us`, `in`, `au`, or `uae`.
- Request Headers: 
  - Please change the `<accessToken>` in the (Product) `x-api-key` or (Space) `Authorization` value with your generated access token in grid console.


## Request authentication
- In Grid Console, you need to generate an Access Token under the "Developer" tab.
- Add `x-api-key` in the request header, with the generated access token value.

## URL's overview

The `{base-url}` of the Grid Products API depends on the data residency you're working with. Make sure you use the correct URL for the data residency you're working with.

| Region | URL                                              |
| ------ | ------------------------------------------------ |
| EU     | `https://product-eu.omborigrid.com/api/tenants`  |
| US     | `https://product-us.omborigrid.com/api/tenants`  |
| IN     | `https://product-in.omborigrid.com/api/tenants`  |
| AU     | `https://product-au.omborigrid.com/api/tenants`  |
| UAE    | `https://product-uae.omborigrid.com/api/tenants` |

?> `{tenant-id}` is your tenant id in the grid console. <br> `{environment}` is any defined environment you have in grid console where you want your products data to live.

The following endpoints are available in the API currently.

| Method | Endpoint                                                                | Description                                                          |
| ------ | ----------------------------------------------------------------------- | -------------------------------------------------------------------- |
| GET    | [products](/grid-products/api?id=get-post-products)                     | Returns list of products based on specified query parameters         |
| GET    | [products/{id}](/grid-products/api?id=get-product-by-id)                | Retrieves specific product by ID                                     |
| GET    | [products-barcode/{code}](/grid-products/api?id=get-product-by-barcode) | Retrieves specific product by barcode value                          |
| GET    | [search](/grid-products/api?id=get-search)                              | Searches products or product types by keyword                        |
| POST   | [products/push](/grid-products/api?id=post-push-products)               | Pushes products into the database                                    |
| DELETE | [products](/grid-products/api?id=delete-remove-products)                | Removes specified product IDs from the database                      |
| PATCH  | [products](/grid-products/api?id=patch-update-products)                 | Update products listed in the database                               |
| PATCH  | [variants](/grid-products/api?id=patch-update-variants)                 | Update variants level information in the database                    |
| GET    | [product-types](/grid-products/api?id=get-product-types-list)           | Returns list of product types associated with the tenant index       |
| GET    | [product-types/{id}](/grid-products/api?id=get-product-type-details)    | Retrieves specific product type by id (ProductTypeId)                |
| POST   | [product-types](/grid-products/api?id=post-push-product-types)          | Pushes product types into the database                               |
| DELETE | [product-types](/grid-products/api?id=delete-remove-product-types)      | Removes specified product type IDs (ProductTypeId) from the database |


# Products
### [GET | POST] Products

> **[GET] {base-url}/{tenant-id}/{environment}/products** <br> **[POST] {base-url}/{tenant-id}/{environment}/products**

Returns a list of products based on specified query parameters.

?> For large requests (>2k characters) we recommend performing the same call using `POST` method instead to avoid URL-length limitations.

#### Response
```
{
     list: Array<Partial<GridProduct>>, 
     count: number,
     facets:  {  [propertyName]: FacetResults[] },
     attributeFilters: { [key]: string[] }
} 
```

Reference: [GridProduct](/grid-products/data-model?id=gridproduct)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter               | type    | Description                                                                                                                            | Example                                               |
| ----------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| search                  | string  | Keyword to search                                                                                                                      | `Desks`                                               |
| searchField             | string  | Specific searchable field to search (one search field at a time only)                                                                  | `productName`                                         |
| limit                   | number  | Maximum number of item count to retrieve `Default: 50`                                                                                 | `100`                                                 |
| page                    | number  | Current pagination result `Default: 1  `                                                                                               | `1`                                                   |
| select                  | string  | List of selected fields to be returned(comma separated)                                                                                | `productGroupId`, `productName`, `productDescription` |
| filter                  | object  | Query string to use for filtering results based on filterable fields.(operators and string values should be enclosed in double quotes) | `{"gt": ["productPriceList/listPrice", 10]}`          |
| sort                    | string  | Sort result order definition ${key} (‘asc’ / 'desc')                                                                                   | `introductionDate asc`, `productGroupId desc`         |
| includeAttributeFilters | boolean | Flag to include in response the filters generated from ProductFeature data of resulting products                                       | true                                                  |
| attributeFilters        | string  | List of ProductFeature.ProductFeatureType that will be generated for resulting filters                                                 | `Dimensions`, `Material`                              |
| facets                  | string  | List of Facetable keys where facets will be returned based on product listing results                                                  | `shellLifeDays`                                       |

### [GET] Product by ID
> **[GET] {base-url}/{tenant-id}/{environment}/products/{productGroupId}**

Retrieves a specific product by ID

#### Response
Returns Partial<[`GridProduct`](/grid-products/data-model?id=gridproduct)>

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter      | type   | Description                                             | Example                                               |
| -------------- | ------ | ------------------------------------------------------- | ----------------------------------------------------- |
| productGroupId | string | The ID of the Product                                   | `100001`                                              |
| select         | string | List of selected fields to be returned(comma separated) | `productGroupId`, `productName`, `productDescription` |

### [GET] Product by Barcode

> **[GET] {base-url}/{tenant-id}/{environment}/products-barcode/{barcode}**

Retrieves a specific product by barcode ID.

Variants checked:
- globalTradeItemNumber
- europeanArticleNumber
- universalProductCode

#### Response
```
{
    productDetails: Partial<GridProduct>,
    productId: string
}
```
Reference: [GridProduct](/grid-products/data-model?id=gridproduct)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                               |
| --------- | ------ | ------------------------------------------------------- | ----------------------------------------------------- |
| barcode   | string | Barcode ID                                              | `0999999999993`                                       |
| select    | string | List of selected fields to be returned(comma separated) | `productGroupId`, `productName`, `productDescription` |

### [GET] Search
> **[GET] {base-url}/{tenant-id}/{environment}/search**

Searches products or product types by keyword

#### Response

```
{ 
    products: Array<Partial<GridProduct>>, 
    productTypes: Array<ProductType>
}
```

Reference: [GridProduct](/grid-products/data-model?id=gridproduct), [ProductType](/grid-products/data-model?id=producttype)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                               |
| --------- | ------ | ------------------------------------------------------- | ----------------------------------------------------- |
| term      | string | Query to search for                                     | `Desk`                                                |
| select    | string | List of selected fields to be returned(comma separated) | `productGroupId`, `productName`, `productDescription` |

### [GET] Product Recommendations by ID
> **[GET] {base-url}/{tenant-id}/{environment}/product-recommendations/{productGroupId}**

Retrieves list of product recommendations taken from RelatedProductGroups field


#### Response

```
Array<Partial<GridProduct>>

```

Reference: [GridProduct](/grid-pim/data-model?id=gridproduct)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter      | type   | Description           | Example  |
| -------------- | ------ | --------------------- | -------- |
| productGroupId | string | The ID of the Product | `100001` |

### [POST] Push Products
> **[POST] {base-url}/{tenant-id}/{environment}/products/push**

Uploads or merges products listing following the GridProduct format

?> Any Product in the pushed set that has a matching productGroupId will overwrite the product

#### Body
The body of the request should be an Array of [GridProducts]((/grid-products/data-model?id=gridproduct)) JSON format using the `content-type` header `application/json`.

| parameter | type                 | Description                                                    | Example |
| --------- | -------------------- | -------------------------------------------------------------- | ------- |
| data      | `Array<GridProduct>` | List of products in GridProduct format to push to the Database |         |

?> Limitations: <br> - 100 products per batch

### [DELETE] Remove Products
> **[DELETE] {base-url}/{tenant-id}/{environment}/products**

Removes products from the Grid Products database based on specified ID's

| parameter | type            | Description                                          | Example            |
| --------- | --------------- | ---------------------------------------------------- | ------------------ |
| data      | `Array<string>` | List of product ID's to be removed from the database | `["1001", "1002"]` |

### [PATCH] Update Products
> **[PATCH] {base-url}/{tenant-id}/{environment}/products**

Updates products with the fields specified in the data object. Shallow-update is performed. Fields not passed in this call will remain the same. Fields containing Arrays or Objects will be completely overwritten.

| parameter | type                          | Description                                                                  |
| --------- | ----------------------------- | ---------------------------------------------------------------------------- |
| data      | `Array<Partial<GridProduct>>` | List of products with fields in GridProduct format to update to the Database |

?> Limitations: <br> - 100 records per batch

Reference: [GridProduct](/grid-products/data-model?id=gridproduct) 

### [PATCH] Update Variants
> **[PATCH] {base-url}/{tenant-id}/{environment}/variants**

Updates variants with the fields specified in the data object without requiring the product's `productGroupId`. Shallow-update is performed. Fields not passed in this call stay the same. Fields containing Arrays or Objects (`productPriceList` and `productItemQuantity`) with the matching specified variant's productId and spaceId only will be upserted.

| parameter      | type                                  | Description                                                                                                                       |
| -------------- | ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| data           | `Array<Partial<VariantUpdateFields>>` | List of variants level information with fields in VariantUpdateFields format to update to the Database                            |
| upsertSpaceIds | boolean                               | Flag to upsert spaceId values from the `productItemQuantity` and `productPriceList` fields to the main product's `spaceIds` field |

Reference: [VariantUpdateFields](/grid-products/data-model?id=variantupdatefields) 

# Product Types

### [GET] Product Types List
> **[GET] {base-url}/{tenant-id}/{environment}/product-types**

Returns list of product types associated with the tenant id and environment

#### Response
Returns Array<[ProductType](/grid-products/data-model?id=producttype)>

| parameter | type   | Description                              | Example         |
| --------- | ------ | ---------------------------------------- | --------------- |
| ids       | string | List of product types ids to be returned | Furniture, Tech |


### [GET] Product Type Details
> **[GET] {base-url}/{tenant-id}/{environment}/product-types/{productTypeId}**

Returns details of a specific product type

#### Response
Returns [ProductType](/grid-products/data-model?id=producttype)

| parameter     | type   | Description                    | Example   |
| ------------- | ------ | ------------------------------ | --------- |
| productTypeId | string | Product type ID to be returned | Furniture |


### [POST] Push Product Types
> **[POST] {base-url}/{tenant-id}/{environment}/product-types**

Update or insert product types to database


#### Response
Returns Array<[OperationResponse](https://docs.microsoft.com/en-us/javascript/api/@azure/cosmos/operationresponse?view=azure-node-latest)>

| parameter | type                 | Description                                                          |
| --------- | -------------------- | -------------------------------------------------------------------- |
| data      | `Array<ProductType>` | List of formatted ProductTypes to push to the Grid Products Database |

?> Limitations: <br> - 100 product types documents per batch<br>

Reference: [ProductType](/grid-products/data-model?id=producttype)

### [DELETE] Remove Product Types
> **[DELETE] {base-url}/{tenant-id}/{environment}/product-types**

Removes product types from the Grid Products database based on specified ids


#### Response
Returns Array<{
    id: string;
    status: number;
}>

| parameter | type            | Description                                                    | Example               |
| --------- | --------------- | -------------------------------------------------------------- | --------------------- |
| data      | `Array<string>` | List of product type IDs to remove from Grid Products database | ["Furniture", "Tech"] |

Reference: [ProductType](/grid-products/data-model?id=producttype)