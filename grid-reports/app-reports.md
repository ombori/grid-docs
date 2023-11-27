## App reports

The following endpoints are available in the API for app reports.

| Method | Endpoint                                                                                    | Description                                                                             |
|--------|---------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| GET    | [events](/grid-reports/app-reports?id=get-app-events)                                       | Returns list of app events based on specified query parameters                          |
| GET    | [sessions](/grid-reports/app-reports?id=get-app-sessions)                                   | Returns list of app sessions based on specified query parameters                        |
| GET    | [nps](/grid-reports/app-reports?id=get-app-nps)                                             | Returns app nps data                                                                    |
| GET    | [events flow](/grid-reports/app-reports?id=get-app-events-flow)                             | Returns app events flow data                                                            |
| GET    | [products events](/grid-reports/app-reports?id=get-app-products-events)                     | Returns list of app products events based on specified query parameters                 |
| GET    | [categories events](/grid-reports/app-reports?id=get-app-categories-events)                 | Returns list of app categories events based on specified query parameters               |
| GET    | [purchases events](/grid-reports/app-reports?id=get-app-purchases-events)                   | Returns list of app purchases (transactions) events based on specified query parameters |
| GET    | [purchased products events](/grid-reports/app-reports?id=get-app-purchased-products-events) | Returns list of app purchased products events based on specified query parameters       |   
| GET    | [qr codes events](/grid-reports/app-reports?id=get-app-qr-codes-events)                     | Returns list of app qr codes events based on specified query parameters                 |   
| GET    | [media events](/grid-reports/app-reports?id=get-app-media-events)                           | Returns list of app media events based on specified query parameters                    | 

?> `{tenant-id}` is your tenant id in the grid console.

?> `{app-id}` is your app id in the grid console.

### [GET] App events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/events**

Returns list of app events based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "appId": string,
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

### [GET] App sessions

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/sessions**

Returns list of app sessions based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "sessionCount": number,
    "date": string,
    "appId": string,
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

### [GET] App nps

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/nps**

Returns app nps data

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

### [GET] App events flow

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/eventsFlow**

Returns app events flow data.

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

### [GET] App products events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/products**

Returns list of app products events based on specified query parameters.

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
    "appId": string
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

### [GET] App categories events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/categories**

Returns list of app categories events based on specified query parameters.

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
    "appId": string
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                                    | Example     | Required |
|-----------------|--------|----------------------------------------------------------------------------------------------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date                                                                                      | 2022-12-26  | true     |
| dateTo          | string | Defines the final date                                                                                         | 2023-01-02  | true     |

### [GET] App purchases events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/purchases**

Returns list of app purchases (transactions) events based on specified query parameters.

#### Response
```
[
  {
    id: string;
    type: string;
    tenantId: string;
    date: string;
    eventType: string;
    eventTime: string;
    interaction: boolean;
    transactionId: string;
    revenue: number;
    currency: string;
    count: number;
    sessionCount: number;
    appId: string;
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description               | Example     | Required |
|-----------------|--------|---------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date | 2022-12-26  | true     |
| dateTo          | string | Defines the final date    | 2023-01-02  | true     |

### [GET] App purchased products events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/purchased-products**

Returns list of app purchased products events based on specified query parameters.

#### Response
```
[
  {
    id: string;
    type: string;
    tenantId: string;
    date: string;
    eventType: string;
    interaction: boolean;
    transactionId: string;
    productId: string;
    categoryId: string;
    productName: string;
    currency: string;
    quantity: number;
    price: number;
    count: number;
    sessionCount: number;
    appId: string;
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description               | Example     | Required |
|-----------------|--------|---------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date | 2022-12-26  | true     |
| dateTo          | string | Defines the final date    | 2023-01-02  | true     |

### [GET] App qr codes events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/qr-codes**

Returns list of app qr codes events based on specified query parameters.

#### Response
```
[
  {
    id: string;
    type: string;
    tenantId: string;
    date: string;
    eventType: string;
    interaction: boolean;
    qrCodeId: string;
    qrCodeContent: string;
    qrCodeEntryMethod: string;
    qrCodeType: string;
    count: number;
    sessionCount: number;
    appId: string;
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description               | Example     | Required |
|-----------------|--------|---------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date | 2022-12-26  | true     |
| dateTo          | string | Defines the final date    | 2023-01-02  | true     |

### [GET] App media events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/apps/{app-id}/media**

Returns list of app media events based on specified query parameters.

#### Response
```
[
  {
    id: string;
    type: string;
    tenantId: string;
    date: string;
    eventType: string;
    interaction: boolean;
    mediaId: string;
    mediaType: string;
    mediaName: string;
    mediaTags: string[];
    mediaDuration: number;
    count: number;
    sessionCount: number;
    appId: string;
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description               | Example     | Required |
|-----------------|--------|---------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date | 2022-12-26  | true     |
| dateTo          | string | Defines the final date    | 2023-01-02  | true     |
