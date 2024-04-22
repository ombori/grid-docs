## Real-time events report

The following endpoints are available in the API for real-time reports.

| Method | Endpoint                                                                               | Description                                   |
|--------|----------------------------------------------------------------------------------------|-----------------------------------------------|
| GET    | [sessions](/grid-reports/installation-reports?id=get-real-time-sessions)               | Returns list of sessions in the past 24 hours |
| GET    | [events](/grid-reports/installation-reports?id=get-real-time-events)                   | Returns list of events in the past 24 hours   |
| GET    | [latest-event](/grid-reports/installation-reports?id=get-real-time-latest-events)      | Returns list of latest events                 |

?> `{tenant-id}` is your tenant id in the grid console.

### [GET] Real-time Sessions

> **[GET] {base-url}/v2/realtime/session/tenants/{tenant-id}**

Returns list of sessions in the past 24 hours

#### Response
```
[
  {
    tenantId: string;
    sessionId: string;
    sessionCreated: Date;
    environment: string;
    dataResidency: string;
    country: string;
    spaceId: string;
    appId: string;
    appVersion?: string;
    installationVersion?: string;
    installationId: string;
    deviceId?: string;
    clientId: string;
    ip: string;
    locationAccuracy: number;
    latitude: number;
    longitude: number;
    captureId: string;
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description              | Required |
|-----------------|--------|--------------------------|----------|
| installationId  | string | Filter by installationId | No       |
| spaceId         | string | Filter by spaceId        | No       |
| deviceId        | string | Filter by deviceId       | No       |

### [GET] Real-time Events

> **[GET] {base-url}/v2/realtime/event/tenants/{tenant-id}**

Returns list of events in the past 24 hours.

#### Response
```
[
  {
    tenantId: string;
    eventTime: Date;
    dataResidency: string;
    sessionId: string;
    clientId: string;
    eventType: string;
    interaction: boolean;
    ip: string;
    captureId: string;
    productId?: string;
    categoryId?: string;
    int1?: number;
    int2?: number;
    int3?: number;
    int4?: number;
    int5?: number;
    str1?: string;
    str2?: string;
    str3?: string;
    str4?: string;
    str5?: string;
    stateful?: boolean;
    public?: number;
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                       | Required |
|-----------------|--------|-------------------------------------------------------------------|----------|
| installationId  | string | Filter by installationId                                          | No       |
| spaceId         | string | Filter by spaceId                                                 | No       |
| deviceId        | string | Filter by deviceId                                                | No       |
| eventType       | string | Filter by deviceId                                                | No       |
| interactionType | string | "interactive" |  "nonInteractive" | "all" - Default is "all"      | No       |

### [GET] Real-time Latest Events

> **[GET] {base-url}/v2/realtime/latest-event/tenants/{tenant-id}**

Returns list of latest events based on distinct fields. It's designed for monitoring events through grid-signals.

#### Response
```
[
  {
    tenantId: string;
    installationId: string;
    deviceId: string;
    spaceId: string
    eventTime: Date;
    dataResidency: string;
    sessionId: string;
    clientId: string;
    eventType: string;
    interaction: boolean;
    ip: string;
    captureId: string;
    productId?: string;
    categoryId?: string;
    int1?: number;
    int2?: number;
    int3?: number;
    int4?: number;
    int5?: number;
    str1?: string;
    str2?: string;
    str3?: string;
    str4?: string;
    str5?: string;
    stateful?: boolean;
    public?: number;
  }
]
```

#### Query Parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                           | Required |
|-----------------|--------|---------------------------------------------------------------------------------------|----------|
| distinctColumns | string | "str1" | "str2" | "str3" | "str4 | "str5" | "int1" | "int2" | "int3" | "int4 | "int5" | Yes      |
| installationId  | string | Filter by installationId                                                              | No       |
| spaceId         | string | Filter by spaceId                                                                     | No       |
| deviceId        | string | Filter by deviceId                                                                    | No       |
| eventType       | string | Filter by deviceId                                                                    | No       |
| interactionType | string | "interactive" |  "nonInteractive" | "all" - Default is "all"                          | No       |
