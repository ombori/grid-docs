## Installation reports

The following endpoints are available in the API for installation reports.

| Method | Endpoint                                                                                      | Description                                                                        |
|--------|-----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| GET    | [events](/grid-reports/installation-reports?id=get-installation-events)                       | Returns list of installation events based on specified query parameters            |
| GET    | [sessions](/grid-reports/installation-reports?id=get-installation-sessions)                   | Returns list of installation sessions based on specified query parameters          |
| GET    | [nps](/grid-reports/installation-reports?id=get-installation-nps)                             | Returns installation nps data                                                      |
| GET    | [events flow](/grid-reports/installation-reports?id=get-installation-events-flow)             | Returns installation events flow data                                              |
| GET    | [products events](/grid-reports/installation-reports?id=get-installation-products-events)     | Returns list of installation products events based on specified query parameters   |
| GET    | [categories events](/grid-reports/installation-reports?id=get-installation-categories-events) | Returns list of installation categories events based on specified query parameters |

?> `{tenant-id}` is your tenant id in the grid console.

?> `{installation-id}` is your installation id in the grid console.

### [GET] Installation events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/installations/{installation-id}/events**

Returns list of installation events based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "installationId": string,
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

### [GET] Installation sessions

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/installations/{installation-id}/sessions**

Returns list of installation sessions based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "sessionCount": number,
    "date": string,
    "installationId": string,
    "hour"?: number
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

### [GET] Installation nps

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/installations/{installation-id}/nps**

Returns installation nps data

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

### [GET] Installation events flow

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/installations/{installation-id}/eventsFlow**

Returns installation events flow data.

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

### [GET] Installation products events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/installations/{installation-id}/products**

Returns list of installation products events based on specified query parameters.

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
    "installationId": string
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

### [GET] Installation categories events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/installations/{installation-id}/categories**

Returns list of installation categories events based on specified query parameters.

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
    "installationId": string
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                                    | Example     | Required |
|-----------------|--------|----------------------------------------------------------------------------------------------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date                                                                                      | 2022-12-26  | true     |
| dateTo          | string | Defines the final date                                                                                         | 2023-01-02  | true     |
