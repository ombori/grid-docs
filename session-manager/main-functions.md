# List of Main Functions

- [init](session-manager/main-functions?id=init)
- [createSession](session-manager/main-functions?id=createsession)
- [trackEvent](undefined)
- [getInstance](undefined)

## init

▸ `Const` **init**(`params`): Promise<void\>

Initialize session manager instance

#### Parameters

| Key                    | Type     | Description                                                                                   | Required | Options            |
| ---------------------- | -------- | --------------------------------------------------------------------------------------------- | -------- | ------------------ |
| tenantId               | string   | Tenant id in the Grid Console                                                                 | yes      |                    |
| environment            | string   | Application environment                                                                       | yes      |                    |
| dataResidency          | string   | The region where to store the data                                                            | yes      | "EU", "UAE", "IN", "US", "AU"  |
| country                | string   | Tenant base country (Abbrev.)                                                                  | yes      |                    |
| spaceId                | string   | The id of the Space where the device or any entity is located                                 | yes      |                    |
| appId                  | string   | The id of the gridapp which is running on a device                                            | yes      |                    |
| appVersion             | string   | List of Product Type IDs applicable to this product as a reference from ProductTypes Database | yes      |                    |
| installationId         | string   | The id of the installation in Grid Console                                                    | yes      |                    |
| installationVersion    | string   | Build id of the installation                                                                  | yes      |                    |
| deviceId               | string   | Id of the device in console. If deviceId is not passed, virtual deviceId is created           | no       |                    |
| clientUserAgent        | string   | Requestor user agent                                                                          | yes      |                    |
| locationAccuracy       | number   | Geographic coordinates accuracy                                                               | no       |                    |
| latitude               | number   | Geographic latitude of the device or requestor                                                | no       | -90 to 90          |
| longitude              | number   | Geographic longitude of the device or requestor                                               | no       | -180 to 180        |
### Returns

Promise<void\>


## createSession

▸ `Const` **createSession**(): Promise<void\>

Start a new session. This will send a SESSION_START event to the analytics service

### Returns

Promise<void\>

___

## trackEvent

▸ `Const` **trackEvent**(`eventParams`): Promise<void\>

Used for tracking custom  events outside the standard session event methods.

#### Event Parameters

| Key                    | Type     | Description                                                                                   | Required |
| ---------------------- | -------- | --------------------------------------------------------------------------------------------- | -------- |
| eventType              | string   | Event type outside the standard event types (Example: TEST_EVENT)                             | yes      |
| interaction            | boolean  | If the event is triggered by a user                                                           | yes      |
| productId              | string   | Product id related to the event                                                               | no       |
| categoryId             | string   | Category id related to the event                                                              | no       |
| int1                   | number   | Integer type field related to the event                                                       | no       |
| int2                   | number   | Integer type field related to the event                                                       | no       |
| int3                   | number   | Integer type field related to the event                                                       | no       |
| int4                   | number   | Integer type field related to the event                                                       | no       |
| int5                   | number   | Integer type field related to the event                                                       | no       |
| str1                   | string   | String type field related to the event                                                        | no       |
| str2                   | string   | String type field related to the event                                                        | no       |
| str3                   | string   | String type field related to the event                                                        | no       |
| str4                   | string   | String type field related to the event                                                        | no       |
| str5                   | string   | String type field related to the event                                                        | no       |
### Returns

Promise<void\>

___
## getInstance

▸ `Const` **getInstance**(): Instance

Get Grid Session current instance

### Returns

Instance

| Key                    | Type     | Description                                                                                  
| ---------------------- | -------- | --------------------------------------------------------------------------------------------- |
| tenantId               | string   | Tenant id in the Grid Console                                                                 |
| sessionId              | string   | Grid Session instance id                                                                      |
| environment            | string   | Application environment                                                                       |
| dataResidency          | string   | The region where to store the data                                                            |
| country                | string   | Tenant base country (Abbrev.)                                                                  |
| spaceId                | string   | The id of the Space where the device or any entity is located                                 |
| appId                  | string   | The id of the gridapp which is running on a device                                            |
| appVersion             | string   | List of Product Type IDs applicable to this product as a reference from ProductTypes Database |
| installationId         | string   | The id of the installation in Grid Console                                                    |
| installationVersion    | string   | Build id of the installation                                                                  |
| deviceId               | string \| undefined   | Id of the device in console. If deviceId is not passed, virtual deviceId is created |
| clientId               | string   | Client id of the requestor. clientId is same as deviceId for registered devices in console    |
| clientCreated          | string   | Date when the client id is created                                                            |
| clientUserAgent        | string   | Requestor user agent                                                                          |                               
| locationAccuracy       | number \| undefined   | Geographic coordinates accuracy                                                   |
| latitude               | number \| undefined   | Geographic latitude of the device or requestor                                    |
| longitude              | number \| undefined   | Geographic longitude of the device or requestor                                   |
