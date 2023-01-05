## Space reports

The following endpoints are available in the API for space reports.

| Method | Endpoint                                                                        | Description                                                                 |
|--------|---------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| GET    | [events](/grid-reports/space-reports?id=get-space-events)                       | Returns list of space events based on specified query parameters            |
| GET    | [sessions](/grid-reports/space-reports?id=get-space-sessions)                   | Returns list of space sessions based on specified query parameters          |
| GET    | [nps](/grid-reports/space-reports?id=get-space-nps)                             | Returns space nps data                                                      |
| GET    | [events flow](/grid-reports/space-reports?id=get-space-events-flow)             | Returns space events flow data                                              |
| GET    | [products events](/grid-reports/space-reports?id=get-space-products-events)     | Returns list of space products events based on specified query parameters   |
| GET    | [categories events](/grid-reports/space-reports?id=get-space-categories-events) | Returns list of space categories events based on specified query parameters |

?> `{tenant-id}` is your tenant id in the grid console.

?> `{space-id}` is your space id in the grid console.

### [GET] Space events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/spaces/{space-id}/events**

Returns list of space events based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "spaceId": string,
    "date": string,
    "eventType": string,
    "interaction": boolean,
    "count": number,
    "sessionCount": number,
    "hour"?: number
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                                    | Example     | Required |
|-----------------|--------|----------------------------------------------------------------------------------------------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date                                                                                      | 2022-12-26  | true     |
| dateTo          | string | Defines the final date                                                                                         | 2023-01-02  | true     |
| interactionType | string | Defines events interaction type. <br>Possible values: `interactive, nonInteractive, all`. Default value: `all` | interactive | false    |
| timespanType    | string | Defines events timespan type. <br>Possible values: `day, hour`. Default value: `day`                           | day         | false    |

### [GET] Space sessions

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/spaces/{space-id}/sessions**

Returns list of space sessions based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "sessionCount": number,
    "date": string,
    "spaceId": string,
    "hour"?: string
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                      | Example       | Required |
|-----------------|--------|--------------------------------------------------------------------------------------------------|---------------|----------|
| dateFrom        | string | Defines the starting date                                                                        | 2022-12-26    | true     |
| dateTo          | string | Defines the final date                                                                           | 2023-01-02    | true     |
| interactionType | string | Defines sessions interaction type. <br>Possible values: `interactive, all`. Default value: `all` | interactive   | false    |
| timespanType    | string | Defines sessions timespan type. <br>Possible values: `day, hour`. Default value: `day`           | day           | false    |

### [GET] Space nps

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/spaces/{space-id}/nps**

Returns space nps data

#### Response
```
{
  "score": number,
  "replyCount": number
}
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                      | Example       | Required |
|-----------------|--------|--------------------------------------------------------------------------------------------------|---------------|----------|
| dateFrom        | string | Defines the starting date                                                                        | 2022-12-26    | true     |
| dateTo          | string | Defines the final date                                                                           | 2023-01-02    | true     |

### [GET] Space events flow

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/spaces/{space-id}/eventsFlow**

Returns space events flow data.

#### Response
```
[
  {
    "count": number,
    "eventType": string,
    "eventTypePrevious"?: string,
    "eventOrder": number
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                             | Example    | Required |
|-----------------|--------|-----------------------------------------------------------------------------------------|------------|----------|
| dateFrom        | string | Defines the starting date                                                               | 2022-12-26 | true     |
| dateTo          | string | Defines the final date                                                                  | 2023-01-02 | true     |
| eventsFlowDepth | number | Defines events flow depth. Minimum value: `1`. Maximum value: `40`. Default value: `15` | 15         | false    |

### [GET] Space products events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/spaces/{space-id}/products**

Returns list of space products events based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "date": string,
    "eventType": string,
    "interaction": boolean,
    "productId": string,
    "count": number,
    "sessionCount": number,
    "spaceId": string
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                                    | Example     | Required |
|-----------------|--------|----------------------------------------------------------------------------------------------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date                                                                                      | 2022-12-26  | true     |
| dateTo          | string | Defines the final date                                                                                         | 2023-01-02  | true     |
| interactionType | string | Defines events interaction type. <br>Possible values: `interactive, nonInteractive, all`. Default value: `all` | interactive | false    |

### [GET] Space categories events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/spaces/{space-id}/categories**

Returns list of space categories events based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "date": string,
    "eventType": string,
    "interaction": boolean,
    "categoryId": string,
    "count": number,
    "sessionCount": number,
    "spaceId": string
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                                    | Example     | Required |
|-----------------|--------|----------------------------------------------------------------------------------------------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date                                                                                      | 2022-12-26  | true     |
| dateTo          | string | Defines the final date                                                                                         | 2023-01-02  | true     |
