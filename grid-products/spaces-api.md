# Spaces API Reference

This is the API reference for Spaces integration. 

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
- You then need to add "Authorization" in the API request header, with the `Bearer <access token>` as value for the SPACES related endpoints below.

## URL's overview

Grid Admin API:
https://api.omborigrid.com/api


> In every endpoint you will need to replace `{base-url}` with the URL specified above.


The following endpoints are available in the Spaces API currently.

| Method | Endpoint                                                        | Description                                  |
| ------ | --------------------------------------------------------------- | -------------------------------------------- |
| GET    | [spaces](/grid-products/spaces-api?id=get-spaces)               | Returns a list of tenant's spaces            |
| GET    | [spaces/{id}](/grid-products/spaces-api?id=get-get-space-by-id) | Retrieves specific space by ID               |
| POST   | [spaces](/grid-products/spaces-api?id=post-space)               | Creates a space record into the database     |
| DELETE | [spaces](/grid-products/spaces-api?id=delete-remove-space)      | Removes specified space ID from the database |
| PUT    | [spaces](/grid-products/api?id=put-update-space)                | Update specified space in the database       |
|        |


# Spaces
### [GET] Spaces List
> **[GET] {base-url}/spaces**

Returns a list of tenant's spaces.

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter      | type   | Description                   | Example              |
| -------------- | ------ | ----------------------------- | -------------------- |
| organizationId | string | The tenant id in grid console | `61cxxxxxxxxxxxxxxx` |

#### Response
```
Array<Space>
```

### [GET] Get Space by ID
> **[GET] {base-url}/spaces/{id}**

Retrieves specific space by ID.

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description         | Example              |
| --------- | ------ | ------------------- | -------------------- |
| id        | string | The ID of the space | `61cxxxxxxxxxxxxxxx` |

#### Response
```
Space
```
Reference: [Space](/grid-products/data-model?id=space)

### [POST] Create Space
> **[POST] {base-url}/spaces**

Creates a space record

#### Body
The body of the request should be a [Space]((/grid-products/data-model?id=space)) JSON format using the `content-type` header `application/json`.

| parameter      | type   | Description                                             | Example              |
| -------------- | ------ | ------------------------------------------------------- | -------------------- |
| organizationId | string | The organization/tenant where the space will be created | `61cxxxxxxxxxxxxxxx` |
| displayName    | string | The name of the space to be displayed                   | `Store #1`           |
| type           | string | The type of the space (`location`,`section`,`custom`) | `location` |
| longitude      | number | Longitude of the space                                  | `59.32960273523599`  |
| latitude       | number | Latitude of the space                                   | `18.06886331765492`  |
| externalId     | string | Id of the space managed externally                      | `store_1`            |

#### Response
```
Space
```

Reference: [Space](/grid-products/data-model?id=space)

### [PUT] Update Space
> **[PUT] {base-url}/spaces/{id}**

Updates a space record

#### Query Parameters
| parameter | type   | Description         | Example              |
| --------- | ------ | ------------------- | -------------------- |
| id        | string | The ID of the space | `61cxxxxxxxxxxxxxxx` |

#### Body
The body of the request should be a [Space]((/grid-products/data-model?id=space)) JSON format using the `content-type` header `application/json`.

| parameter      | type   | Description                                             | Example              |
| -------------- | ------ | ------------------------------------------------------- | -------------------- |
| organizationId | string | The organization/tenant where the space will be created | `61cxxxxxxxxxxxxxxx` |
| displayName    | string | The name of the space to be displayed                   | `Store #1`           |
| type           | string | The type of the space ('location'                       | 'section'            | 'custom') | `location` |
| longitude      | number | Longitude of the space                                  | `59.32960273523599`  |
| latitude       | number | Latitude of the space                                   | `18.06886331765492`  |
| externalId     | string | Id of the space managed externally                      | `store_1`            |

#### Response
```
Space
```

Reference: [Space](/grid-products/data-model?id=space)

### [DELETE] Remove Space
> **[DELETE] {base-url}/spaces/{id}**

Deletes a space record

#### Query Parameters
| parameter | type   | Description         | Example              |
| --------- | ------ | ------------------- | -------------------- |
| id        | string | The ID of the space | `61cxxxxxxxxxxxxxxx` |

#### Response
```
Space
```

Reference: [Space](/grid-products/data-model?id=space)
