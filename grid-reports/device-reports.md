## Device reports

The following endpoints are available in the API for device reports.

| Method | Endpoint                                                                          | Description                                                                  |
|--------|-----------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| GET    | [events](/grid-reports/device-reports?id=get-device-events)                       | Returns list of device events based on specified query parameters            |
| GET    | [sessions](/grid-reports/device-reports?id=get-device-sessions)                   | Returns list of device sessions based on specified query parameters          |
| GET    | [nps](/grid-reports/device-reports?id=get-device-nps)                             | Returns device nps data                                                      |
| GET    | [events flow](/grid-reports/device-reports?id=get-device-events-flow)             | Returns device events flow data                                              |
| GET    | [products events](/grid-reports/device-reports?id=get-device-products-events)     | Returns list of device products events based on specified query parameters   |
| GET    | [categories events](/grid-reports/device-reports?id=get-device-categories-events) | Returns list of device categories events based on specified query parameters |

?> `{tenant-id}` is your tenant id in the grid console.

?> `{device-id}` is your device id in the grid console.

### [GET] Device events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/devices/{device-id}/events**

Returns list of device events based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "deviceId": string,
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

### [GET] Device sessions

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/devices/{device-id}/sessions**

Returns list of device sessions based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "sessionCount": number,
    "date": string,
    "deviceId": string,
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

### [GET] Device nps

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/devices/{device-id}/nps**

Returns device nps data

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

### [GET] Device events flow

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/devices/{device-id}/eventsFlow**

Returns device events flow data.

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

### [GET] Device products events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/devices/{device-id}/products**

Returns list of device products events based on specified query parameters.

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
    "deviceId": string
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

### [GET] Device categories events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/devices/{device-id}/categories**

Returns list of device categories events based on specified query parameters.

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
    "deviceId": string
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                                    | Example     | Required |
|-----------------|--------|----------------------------------------------------------------------------------------------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date                                                                                      | 2022-12-26  | true     |
| dateTo          | string | Defines the final date                                                                                         | 2023-01-02  | true     |
