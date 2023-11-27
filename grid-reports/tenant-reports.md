## Tenant reports

The following endpoints are available in the API for tenant reports.

| Method | Endpoint                                                                                          | Description                                                                                |
|--------|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| GET    | [events](/grid-reports/tenant-reports?id=get-tenant-events)                                       | Returns list of tenant events based on specified query parameters                          |
| GET    | [sessions](/grid-reports/tenant-reports?id=get-tenant-sessions)                                   | Returns list of tenant sessions based on specified query parameters                        |
| GET    | [nps](/grid-reports/tenant-reports?id=get-tenant-nps)                                             | Returns tenant nps data                                                                    |
| GET    | [events flow](/grid-reports/tenant-reports?id=get-tenant-events-flow)                             | Returns tenant events flow data                                                            |
| GET    | [products events](/grid-reports/tenant-reports?id=get-tenant-products-events)                     | Returns list of tenant products events based on specified query parameters                 |
| GET    | [categories events](/grid-reports/tenant-reports?id=get-tenant-categories-events)                 | Returns list of tenant categories events based on specified query parameters               |
| GET    | [purchases events](/grid-reports/tenant-reports?id=get-tenant-purchases-events)                   | Returns list of tenant purchases (transactions) events based on specified query parameters |
| GET    | [purchased products events](/grid-reports/tenant-reports?id=get-tenant-purchased-products-events) | Returns list of tenant purchased products events based on specified query parameters       |   
| GET    | [qr codes events](/grid-reports/tenant-reports?id=get-tenant-qr-codes-events)                     | Returns list of tenant qr codes events based on specified query parameters                 |   
| GET    | [media events](/grid-reports/tenant-reports?id=get-tenant-media-events)                           | Returns list of tenant media events based on specified query parameters                    |   

?> `{tenant-id}` is your tenant id in the grid console.

### [GET] Tenant events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/events**

Returns list of tenant events based on specified query parameters.

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

### [GET] Tenant sessions

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/sessions**

Returns list of tenant sessions based on specified query parameters.

#### Response
```
[
  {
    "id": string,
    "type": string,
    "tenantId": string,
    "sessionCount": number,
    "date": string,
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

### [GET] Tenant nps

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/nps**

Returns tenant nps data

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

### [GET] Tenant events flow

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/eventsFlow**

Returns tenant events flow data.

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

### [GET] Tenant products events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/products**

Returns list of tenant products events based on specified query parameters.

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
    "sessionCount": number
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

### [GET] Tenant categories events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/categories**

Returns list of tenant categories events based on specified query parameters.

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
    "sessionCount": number
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                                                    | Example     | Required |
|-----------------|--------|----------------------------------------------------------------------------------------------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date                                                                                      | 2022-12-26  | true     |
| dateTo          | string | Defines the final date                                                                                         | 2023-01-02  | true     |

### [GET] Tenant purchases events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/purchases**

Returns list of tenant purchases (transactions) events based on specified query parameters.

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
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description               | Example     | Required |
|-----------------|--------|---------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date | 2022-12-26  | true     |
| dateTo          | string | Defines the final date    | 2023-01-02  | true     |

### [GET] Tenant purchased products events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/purchased-products**

Returns list of tenant purchased products events based on specified query parameters.

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
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description               | Example     | Required |
|-----------------|--------|---------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date | 2022-12-26  | true     |
| dateTo          | string | Defines the final date    | 2023-01-02  | true     |

### [GET] Tenant qr codes events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/qr-codes**

Returns list of tenant qr codes events based on specified query parameters.

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
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description               | Example     | Required |
|-----------------|--------|---------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date | 2022-12-26  | true     |
| dateTo          | string | Defines the final date    | 2023-01-02  | true     |

### [GET] Tenant media events

> **[GET] {base-url}/v2/report/tenants/{tenant-id}/media**

Returns list of tenant media events based on specified query parameters.

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
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description               | Example     | Required |
|-----------------|--------|---------------------------|-------------|----------|
| dateFrom        | string | Defines the starting date | 2022-12-26  | true     |
| dateTo          | string | Defines the final date    | 2023-01-02  | true     |
