# Spaces API Reference

This is the API reference for Spaces integration. 

## Postman Collection
For easy configuration and testing, here's a Postman collection you can import into Postman.
// TODO: New postman collection

## Request authentication
- In Grid Console, you need to generate an Access Token under the "Developer" tab.
- You then need to add "Authorization" in the request header, with the `Bearer <access token>` as value for the SPACES related endpoints below.

## URL's overview

Grid Admin API:
https://api.omborigrid.com


> In every endpoint you will need to replace `{base-url}` with the URL specified above.


The following endpoints are available in the Spaces API currently.

| Method | Endpoint                                                                | Description                                                          |
| ------ | ----------------------------------------------------------------------- | -------------------------------------------------------------------- |
| GET    | [spaces](/grid-products/spaces-api?id=get-spaces)                     | Returns a list of tenant's spaces         |
| GET    | [spaces/{id}](/grid-products/spaces-api?id=get-space-by-id)                | Retrieves specific space by ID                                     |
| POST   | [spaces](/grid-products/spaces-api?id=post-space)               | Creates a space record into the database                                    |
| DELETE | [spaces](/grid-products/spaces-api?id=delete-space)                | Removes specified space ID from the database                      |
| PUT  | [spaces](/grid-products/api?id=put-update-space)                 | Update specified space in the database                               |
|


# Spaces
### [GET] Spaces

> **[GET] {base-url}/spaces**
Returns a list of tenant's spaces.

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                             | Example                                          |
| --------- | ------ | ------------------------------------------------------- | ------------------------------------------------ |
| organizationId | string | The tenant id in grid console                                   | `61cxxxxxxxxxxxxxxx`                                         |

#### Response
```
Array<Space & { id: string }>
```

Reference: [Space](/grid-products/data-model?id=space)

