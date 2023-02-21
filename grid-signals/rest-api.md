# Grid Signals REST API

Today, Grid Signals client libraries support only javascript and NodeJS based projects. We are planning to expand it to support more languages, like python.

Meanwhile, you can directly use the Grid Signals REST API.

## Base urls
Grid Signals has multiple instances based on data residency. Below are the base urls:
- AU: https://signal-au.omborigrid.com/api
- EU: https://signal-eu.omborigrid.com/api
- IN: https://signal-in.omborigrid.com/api
- UAE: https://signal-uae.omborigrid.com/api
- US: https://signal-us.omborigrid.com/api

## API endpoints
When sending events to the endpoints, the keys should be parsed and shortened based on the [Key Table](/grid-signals/rest-api?id=key-table)
- [Creating a Session](/grid-signals/rest-api?id=creating-a-session)
- [Sending a Client Information](/grid-signals/rest-api?id=sending-a-client-information)
- [Sending an Event](/grid-signals/rest-api?id=sending-an-event)


### Creating a Session
route: /event

| Key                 | Type   | Description                                                                                   | Required | Options                       |
| ------------------- | ------ | --------------------------------------------------------------------------------------------- | -------- | ----------------------------- |
| sessionId           | string | Version 4 UUID string                                                                         | yes      |                               |
| sessionCreated      | string | Date string format session creation date time                                                 | yes      |                               |
| tenantId            | string | Tenant id in the Grid Console                                                                 | yes      |                               |
| environment         | string | Application environment                                                                       | yes      |                               |
| dataResidency       | string | The region where to store the data                                                            | yes      | "EU", "UAE", "IN", "US", "AU" |
| country             | string | Tenant base country (Abbrev.)                                                                 | yes      |                               |
| spaceId             | string | The id of the Space where the device or any entity is located                                 | yes      |                               |
| appId               | string | The id of the gridapp which is running on a device                                            | yes      |                               |
| appVersion          | string | List of Product Type IDs applicable to this product as a reference from ProductTypes Database | yes      |                               |
| installationId      | string | The id of the installation in Grid Console                                                    | yes      |                               |
| installationVersion | string | Build id of the installation                                                                  | yes      |                               |
| deviceId            | string | Id of the device in the console. If deviceId is not passed, virtual deviceId is created       | no       |                               |
| clientId            | string | Browser based device ID for mobile pwa apps                                                   | no       |                               |
| locationAccuracy    | number | Geographic coordinates accuracy                                                               | no       |                               |
| latitude            | number | Geographic latitude of the device or requestor                                                | no       | -90 to 90                     |
| longitude           | number | Geographic longitude of the device or requestor                                               | no       | -180 to 180                   |

### Sending a Client Information
For mobile pwa apps, you need to send client data to Grid Signals

route: /client

| Key                 | Type   | Description                                                                                   | Required | Options                       |
| ------------------- | ------ | --------------------------------------------------------------------------------------------- | -------- | ----------------------------- |
| tenantId            | string | Tenant id in the Grid Console                                                                 | yes      |                               |
| clientId            | string | Browser based device ID for mobile pwa apps                                                   | yes      |                               |
| clientCreated       | string | Date string format session creation date time                                                 | yes      |                               |
| clientUserAgent     | string | Browser user-agent                                                                            | yes      |                               |
| dataResidency       | string | The region where to store the data                                                            | yes      | "EU", "UAE", "IN", "US", "AU" |
| country             | string | Tenant base country (Abbrev.)                                                                 | yes      |                               |
| locationAccuracy    | number | Geographic coordinates accuracy                                                               | no       |                               |
| latitude            | number | Geographic latitude of the device or requestor                                                | no       | -90 to 90                     |
| longitude           | number | Geographic longitude of the device or requestor                                               | no       | -180 to 180                   |
| clientScreenWidth   | number | Device screen width                                                                           | no       |                               |
| clientScreenHeight  | number | Device screen height                                                                          | no       |                               |
| clientScreenColorDepth  | number | Device screen color depth                                                                 | no       |                               |
| clientScreenPixelDepth  | number | Device screen pixel depth                                                                 | no       |                               |

### Sending an Event

route: /event

| Key         | Type    | Description                                                       | Required |
| ----------- | ------- | ----------------------------------------------------------------- | -------- |
| sessionId   | string  | Version 4 UUID string                                             | yes      |
| tenantId    | string  | Tenant id in the Grid Console                                     | yes      |
| eventType   | string  | Event type (Example: TEST_EVENT)                                  | yes      |
| eventTime   | string  | Date string format of when the event was triggered                | yes      |
| interaction | boolean | Flag if the event is user triggered event                         | yes      |
| dataResidency | string | The region where to store the data                               | yes      |
| productId   | string  | Product id related to the event                                   | no       |
| categoryId  | string  | Category id related to the event                                  | no       |
| clientId            | string | Browser based device ID for mobile pwa apps                | no       |
| int1        | number  | Integer type field related to the event                           | no       |
| int2        | number  | Integer type field related to the event                           | no       |
| int3        | number  | Integer type field related to the event                           | no       |
| int4        | number  | Integer type field related to the event                           | no       |
| int5        | number  | Integer type field related to the event                           | no       |
| str1        | string  | String type field related to the event                            | no       |
| str2        | string  | String type field related to the event                            | no       |
| str3        | string  | String type field related to the event                            | no       |
| str4        | string  | String type field related to the event                            | no       |
| str5        | string  | String type field related to the event                            | no       |
| stateful    | boolean | If the event should be persisted as a state                       | no       |
| public      | boolean | Public state expiry duration                                      | no       |


## Key Table
| Original Parameter          | Shortened Parameter         |
| --------------------------- | --------------------------- |
| captureId                   | a                           |
| sessionId                   | b                           |
| tenantId                    | c                           |
| sessionCreated              | d                           |
| ip:                         | e                           |
| environment                 | f                           |   
| dataResidency               | g                           |
| spaceId                     | h                           |
| appId                       | i                           |
| appVersion                  | j                           |
| installationId              | k                           |
| installationVersion         | l                           |
| country                     | m                           |
| locationAccuracy            | n                           |
| latitude                    | o                           |
| longitude                   | p                           |
| deviceId                    | q                           |
| clientId                    | r                           |
| eventType:                  | s                           |
| eventTime                   | t                           |
| interaction                 | u                           |
| productId                   | v                           |
| categoryId                  | w                           |
| int1                        | x                           |
| int2                        | y                           |
| int3                        | z                           |
| int4                        | aa                          |
| int5                        | ab                          |
| str1                        | ac                          |
| str2                        | ad                          |
| str3                        | ae                          |
| str4                        | af                          |
| str5                        | ag                          |
| clientCreated               | ah                          |
| clientIp                    | ai                          |
| clientUserAgent             | aj                          |
| clientDeviceVendor          | ak                          |
| clientDeviceModel           | al                          |
| clientDeviceType            | am                          |
| clientOsName                | an                          |
| clientOsVersion             | ao                          |
| clientBrowserName           | ap                          |
| clientBrowserVersion        | aq                          |
| clientBrowserMajor          | ar                          |
| clientBrowserEngine         | as                          |
| clientBrowserEngineVersion  | at                          |
| clientCpuArchitecture       | au                          |
| clientScreenWidth           | av                          |
| clientScreenHeight          | aw                          |
| clientScreenColorDepth      | ax                          |
| clientScreenPixelDepth      | ay                          |
| stateful                    | ba                          |
| public                      | bb                          |

- [getSessionState](/grid-signals/states-and-events?id=getsessionstate)
- [getSpaceState](/grid-signals/states-and-events?id=getspacestate)
- [getSpaceStateRows](/grid-signals/states-and-events?id=getspacestaterows)
- [subscribeSessionState](/grid-signals/states-and-events?id=subscribesessionstate)
- [subscribeSessionEvent](/grid-signals/states-and-events?id=subscribesessionevent)
- [subscribeSessionEvent](/grid-signals/states-and-events?id=subscribespacestate)
- [subscribeSpaceEvent](/grid-signals/states-and-events?id=subscribespaceevent)
