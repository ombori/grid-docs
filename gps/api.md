# GPS API Reference

This is the API reference for the GPS integration. 

## Postman Collection
For easy configuration and testing, here's a Postman collection you can import into Postman.

> Download our [Postman Collection](https://www.getpostman.com/collections/80d6e41ef0aaaf9f1887) that's linked to the dev environent with a dev database

## URL's overview
?> For testing purposes, use the following DEV base URL `https://grid-product-service-dev.azurewebsites.net/api/tenants`.

?> With the creation of your tenant a tenant index name will be generated for you, if you do not have this please reach out to your contact within Ombori. Once you've received your Tenant index, you can insert this into the URL's where we've put `{tenant-index}`. 

The following endpoints are available in the API currently.

| Method | Endpoint                             | Description                                                  |
| ------ | ------------------------------------ | ------------------------------------------------------------ |
| GET    | [products](/gps/api?id=get-products) | Returns list of products based on specified query parameters |
| GET    | products/{id}                        | Retrieves specific product by ID                             |
| GET    | products-barcode/{code}           | Retrieves specific product by barcode value                  |
| GET    | search                               | Searches products or product types by keyword                     |
| POST   | products/push                        | Pushes products into the database                            |
| DELETE   | products                      | Removes specified product IDs from the database              |
| PATCH  | products               | Update products listed in the database                       |

# Products Endpoints
### [GET] Products

> **[GET] {base-url}/{tenant-index}/products**

Returns a list of products based on specified query parameters.

#### Response
```
{
     list: Array<GridProduct>, 
     facets:  {  [propertyName]: FacetResults[] },
     attributeFilters: { [key]: string[] }
} 
```
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
| sort                    | string  | Sort result order definition ${key} (‘asc’ / `‘desc'`)                                                                                  | `IntroductionDate asc`, `ProductId desc`         |
| includeAttributeFilters | boolean | Flag to include in response the filters generated from ProductFeature data of resulting products                                       | true                                             |
| attributeFilters        | string  | List of ProductFeature.ProductFeatureType that will be generated for resulting filters                                                 | `Dimensions`, `Material`                         |
| facets                  | string  | List of Facetable keys where facets will be returned based on product listing results                                                  | `ShellLifeDays`                                  |

### [GET] Product by ID
> **[GET] {base-url}/{tenant-index}/products/{productId}**

Retrieves a specific product by ID

#### Response
Returns [GridProduct](/gps/data-model?id=gridproduct)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter  | type   | Description                                             | Example                                          |
| ---------- | ------ | ------------------------------------------------------- | ------------------------------------------------ |
| productId | string | The ID of the Product                                   | `100001`                                         |
| select     | string | List of selected fields to be returned(comma separated) | `ProductId`, `ProductName`, `ProductDescription` |

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
    productDetails: GridProduct,
    variantId: string
}
```
Reference: [GridProduct](/gps/data-model?id=gridproduct)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                          |
| --------- | ------ | ------------------------------------------------------- | ------------------------------------------------ |
| barcode   | string | Barcode ID                                              | `0999999999993`                                  |
| select    | string | List of selected fields to be returned(comma separated) | `ProductId`, `ProductName`, `ProductDescription` |

### [GET] Search
> **[GET] {base-url}/{tenant-index}/search**

?> This endpoint is still in active development

Searches products or product types by keyword


#### Response

!> Currently product types search is a work in progress. They may not be returned or empty

```
{ 
    products: Array<GridProduct>, 
    productTypes: Array<ProductType>
}
```

Reference: [GridProduct](/gps/data-model?id=gridproduct), [ProductType](/gps/data-model?id=producttype)

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                          |
| --------- | ------ | ------------------------------------------------------- | ------------------------------------------------ |
| term      | string | Query to search for                                     | `Desk`                                           |
| select    | string | List of selected fields to be returned(comma separated) | `ProductId`, `ProductName`, `ProductDescription` |

### [POST] Push Products
> **[POST] {base-url}/{tenant-index}/products/push**

Uploads or merges products listing following the GridProduct format

?> Any Product in the pushed set that has a matching ProductId will overwrite the product

#### Body
The body of the request should be an Array of [GridProducts]((/gps/data-model?id=gridproduct)) JSON format using the `content-type` header `application/json`.

?> Limitations: <br> - 1000 product documents per batch<br> - 15MB request limit per batch

### [DELETE] Remove Products
> **[DELETE] {base-url}/{tenant-index}/products**
