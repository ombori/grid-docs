# Grid Products API Reference

This is the API reference for Grid-Products integration. 

## Postman Collection
For easy configuration and testing, here's a Postman collection you can import into Postman.
// TODO: Postman

## URL's overview

The `{base-url}` of the Grid-Products API depends on the environment you're working with.

- EU base URL: `https://product-eu.azurewebsites.net/api/tenants/`
- US base URL: `https://product-us.azurewebsites.net/api/tenants/`
- IN base URL: `https://product-in.azurewebsites.net/api/tenants/`
- AU base URL: `https://product-au.azurewebsites.net/api/tenants/`
- UAE base URL: `https://product-uae.azurewebsites.net/api/tenants/`



> In every endpoint you will need to replace `{base-url}` with the URL specified above.

?> With the creation of your tenant a tenant index name will be generated for you, if you do not have this please reach out to your contact within Ombori. Once you've received your Tenant index, you can insert this into the URL's where you'll see `{tenant-index}`. 

The following endpoints are available in the API currently.

| Method | Endpoint                                                           | Description                                                          |
| ------ | ------------------------------------------------------------------ | -------------------------------------------------------------------- |
| GET    | [products](/grid-pim/api?id=get-post-products)                     | Returns list of products based on specified query parameters         |
| GET    | [products/{id}](/grid-pim/api?id=get-product-by-id)                | Retrieves specific product by ID                                     |
| GET    | [products-barcode/{code}](/grid-pim/api?id=get-product-by-barcode) | Retrieves specific product by barcode value                          |
| GET    | [search](/grid-pim/api?id=get-search)                              | Searches products or product types by keyword                        |
| GET  | [product-recommendations/{id}](/grid-pim/api?id=get-product-recommendations-by-id)                 | Retrieves list of product recommendations by ID                               |
| POST   | [products/push](/grid-pim/api?id=post-push-products)               | Pushes products into the database                                    |
| DELETE | [products](/grid-pim/api?id=delete-remove-products)                | Removes specified product IDs from the database                      |
| PATCH  | [products](/grid-pim/api?id=patch-update-products)                 | Update products listed in the database                               |
| GET    | [product-types](/grid-pim/api?id=get-product-types-list)           | Returns list of product types associated with the tenant index       |
| GET    | [product-types/{id}](/grid-pim/api?id=get-product-type-details)    | Retrieves specific product type by id (ProductTypeId)                |
| POST   | [product-types](/grid-pim/api?id=post-push-product-types)          | Pushes product types into the database                               |
| DELETE | [product-types](/grid-pim/api?id=delete-remove-product-types)      | Removes specified product type IDs (ProductTypeId) from the database |


# Products
### [GET | POST] Products

> **[GET] {base-url}/{tenant-index}/products** <br> **[POST] {base-url}/{tenant-index}/products**

Returns a list of products based on specified query parameters.

?> For large requests (>2k characters) we recommend performing the same call using `POST` method instead to avoid URL-length limitations.

#### Response
```
{
     list: Array<Partial<GridProduct>>, 
     facets:  {  [propertyName]: FacetResults[] },
     attributeFilters: { [key]: string[] }
} 
```

Reference: [GridProduct](/grid-pim/data-model?id=gridproduct)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter               | type    | Description                                                                                                                            | Example                                          |
| ----------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| search                  | string  | Keyword to search                                                                                                                      | `Desks`                                          |
| searchField             | string  | Specific searchable field to search (one search field at a time only)                                                                  | `ProductName`                                    |
| limit                   | number  | Maximum number of item count to retrieve `Default: 50`                                                                                 | `100`                                            |
| page                    | number  | Current pagination result `Default: 1  `                                                                                               | `1`                                              |
| select                  | string  | List of selected fields to be returned(comma separated)                                                                                | `ProductId`, `ProductName`, `ProductDescription` |
| filter                  | object  | Query string to use for filtering results based on filterable fields.(operators and string values should be enclosed in double quotes) | `{"gt": ["ProductPriceList/ListPrice", 10]}`     |
| sort                    | string  | Sort result order definition ${key} (‘asc’ / 'desc')                                                                                   | `IntroductionDate asc`, `ProductId desc`         |
| includeAttributeFilters | boolean | Flag to include in response the filters generated from ProductFeature data of resulting products                                       | true                                             |
| attributeFilters        | string  | List of ProductFeature.ProductFeatureType that will be generated for resulting filters                                                 | `Dimensions`, `Material`                         |
| facets                  | string  | List of Facetable keys where facets will be returned based on product listing results                                                  | `ShellLifeDays`                                  |

### [GET] Product by ID
> **[GET] {base-url}/{tenant-index}/products/{productId}**

Retrieves a specific product by ID

#### Response
Returns Partial<[`GridProduct`](/grid-pim/data-model?id=gridproduct)>

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                          |
| --------- | ------ | ------------------------------------------------------- | ------------------------------------------------ |
| productId | string | The ID of the Product                                   | `100001`                                         |
| select    | string | List of selected fields to be returned(comma separated) | `ProductId`, `ProductName`, `ProductDescription` |

### [GET] Product by Barcode

> **[GET] {base-url}/{tenant-index}/products-barcode/{barcode}**

Retrieves a specific product by barcode ID.

Variants checked:
- GlobalTradeItemNumber
- EuropeanArticleNumber
- UniversalProductCode

#### Response
```
{
    productDetails: Partial<GridProduct>,
    variantId: string
}
```
Reference: [GridProduct](/grid-pim/data-model?id=gridproduct)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                          |
| --------- | ------ | ------------------------------------------------------- | ------------------------------------------------ |
| barcode   | string | Barcode ID                                              | `0999999999993`                                  |
| select    | string | List of selected fields to be returned(comma separated) | `ProductId`, `ProductName`, `ProductDescription` |

### [GET] Search
> **[GET] {base-url}/{tenant-index}/search**

Searches products or product types by keyword

#### Response

```
{ 
    products: Array<Partial<GridProduct>>, 
    productTypes: Array<ProductType>
}
```

Reference: [GridProduct](/grid-pim/data-model?id=gridproduct), [ProductType](/grid-pim/data-model?id=producttype)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                          |
| --------- | ------ | ------------------------------------------------------- | ------------------------------------------------ |
| term      | string | Query to search for                                     | `Desk`                                           |
| select    | string | List of selected fields to be returned(comma separated) | `ProductId`, `ProductName`, `ProductDescription` |

### [GET] Product Recommendations by ID
> **[GET] {base-url}/{tenant-index}/product-recommendations/{productId}**

Retrieves list of product recommendations taken from RelatedProducts field


#### Response

```
Array<Partial<GridProduct>>

```

Reference: [GridProduct](/grid-pim/data-model?id=gridproduct)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                          |
| --------- | ------ | ------------------------------------------------------- | ------------------------------------------------ |
| productId | string | The ID of the Product                                   | `100001`                                         |

### [POST] Push Products
> **[POST] {base-url}/{tenant-index}/products/push**

Uploads or merges products listing following the GridProduct format

?> Any Product in the pushed set that has a matching ProductId will overwrite the product

#### Body
The body of the request should be an Array of [GridProducts]((/grid-pim/data-model?id=gridproduct)) JSON format using the `content-type` header `application/json`.

| parameter | type                 | Description                                                    | Example |
| --------- | -------------------- | -------------------------------------------------------------- | ------- |
| data      | `Array<GridProduct>` | List of products in GridProduct format to push to the Database |         |

?> Limitations: <br> - 100 products per batch

### [DELETE] Remove Products
> **[DELETE] {base-url}/{tenant-index}/products**

Removes products from the Grid-Products database based on specified ID's

| parameter | type            | Description                                          | Example            |
| --------- | --------------- | ---------------------------------------------------- | ------------------ |
| data      | `Array<string>` | List of product ID's to be removed from the database | `[“1001”, “1002”]` |

### [PATCH] Update Products
> **[PATCH] {base-url}/{tenant-index}/products**

Updates products with the fields specified in the data object. Shallow-update is performed. Fields not passed in this call will remain the same. Fields containing Arrays or Objects will be completely overwritten.

| parameter | type                          | Description                                                                  |
| --------- | ----------------------------- | ---------------------------------------------------------------------------- |
| data      | `Array<Partial<GridProduct>>` | List of products with fields in GridProduct format to update to the Database |

Reference: [GridProduct](/grid-pim/data-model?id=gridproduct) 

# Product Types

### [GET] Product Types List
> **[GET] {base-url}/{tenant-index}/product-types**

Returns list of product types associated with the tenant index

#### Response
Returns Array<[ProductType](/grid-pim/data-model?id=producttype)>

| parameter | type   | Description                              | Example         |
| --------- | ------ | ---------------------------------------- | --------------- |
| ids       | string | List of product types ids to be returned | Furniture, Tech |


### [GET] Product Type Details
> **[GET] {base-url}/{tenant-index}/product-types/{productTypeId}**

Returns details of a specific product type

#### Response
Returns [ProductType](/grid-pim/data-model?id=producttype)

| parameter     | type   | Description                    | Example   |
| ------------- | ------ | ------------------------------ | --------- |
| productTypeId | string | Product type ID to be returned | Furniture |


### [POST] Push Product Types
> **[POST] {base-url}/{tenant-index}/product-types**

Update or insert product types to database


#### Response
Returns Array<[OperationResponse](https://docs.microsoft.com/en-us/javascript/api/@azure/cosmos/operationresponse?view=azure-node-latest)>

| parameter | type                 | Description                                                     |
| --------- | -------------------- | --------------------------------------------------------------- |
| data      | `Array<ProductType>` | List of formatted ProductTypes to push to the Grid-Products Database |

?> Limitations: <br> - 100 product types documents per batch<br>

Reference: [ProductType](/grid-pim/data-model?id=producttype)

### [DELETE] Remove Product Types
> **[DELETE] {base-url}/{tenant-index}/product-types**

Removes product types from the Grid-Products database based on specified ids


#### Response
Returns Array<{
    id: string;
    status: number;
}>

| parameter | type            | Description                                               | Example               |
| --------- | --------------- | --------------------------------------------------------- | --------------------- |
| data      | `Array<string>` | List of product type IDs to remove from Grid-Products database | ["Furniture", "Tech"] |

Reference: [ProductType](/grid-pim/data-model?id=producttype)