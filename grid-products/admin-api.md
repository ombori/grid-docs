# Admin API Reference

This is the API reference for get an overview about grid-products. 

## Postman Collection
For easy configuration and testing, here's a Postman collection you can import into Postman.

?> Download the [Postman Collection](https://elements.getpostman.com/redirect?entityId=28975768-13915009-a9d3-4f9c-acde-b8dbbf7e2a12&entityType=collection)

- URL: 
  - Please change the values for `<tenant-id>`, `<environment>`, and `<space-id>`
  - Please change the value of `<data-residency>` with either `eu`, `us`, `in`, `au`, or `uae`.
- Request Headers: 
  - Please change the `x-api-key` in `Authorization` value with your generated access token in grid console.

## Request authentication
- In Grid Console, you need to generate an Access Token under the "Developer" tab.
- You then need to add "Authorization" in the API request header, with the `Bearer <access token>` as value for the Admin related endpoints below.

## URL's overview

Grid Admin API:
https://api.omborigrid.com/api


> In every endpoint you will need to replace `{base-url}` with the URL specified above.

| Method | Endpoint                                                        | Description                                  |
| ------ | --------------------------------------------------------------- | -------------------------------------------- |
| GET    | [admin](/grid-products/admin-api?id=get-spaces)                 | Returns an overview of the products in the space |
|        |


# Space overview
### [GET] Space Overview
> **[GET] {base-url}/admin/overview/{spaceId}**

Returns overview information of tenant's products int the space.

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter      | type   | Description                   | Example              |
| -------------- | ------ | ----------------------------- | -------------------- |
| organizationId | string | The tenant id in grid console | `61cxxxxxxxxxxxxxxx` |
| spaceId        | string | The space id in grid console  | `612cxxxxxxxxxxxxxxx`|

#### Response
```json
{
    "data":{
        "productsCount": 123,
        "variantsCount": 123,
        "productsMissingPricesCount": 123,
        "productsMissingQuantityCount": 123,
        "productsMissingCatalogCount": 123,
        "totalProductsQuantity": 123,
        "productStatus":[
            {
                "status": "<status>",
                "count": 123
            }
        ]
    }
}
```