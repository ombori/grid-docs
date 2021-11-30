# List of Main Functions

- [init](session-manager/main-functions?id=init)
- [createSession](session-manager/main-functions?id=createsession)
- [getInstance](/session-manager/main-functions?id=getinstance)

## init

▸ `Const` **init**(`params`): Promise<void\>

Initialize session manager instance

#### Parameters

| Key                 | Type   | Description                                                                                   | Required | Options                       |
| ------------------- | ------ | --------------------------------------------------------------------------------------------- | -------- | ----------------------------- |
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
| clientUserAgent     | string | Requestor user agent                                                                          | yes      |                               |
| locationAccuracy    | number | Geographic coordinates accuracy                                                               | no       |                               |
| latitude            | number | Geographic latitude of the device or requestor                                                | no       | -90 to 90                     |
| longitude           | number | Geographic longitude of the device or requestor                                               | no       | -180 to 180                   |
### Returns

Promise<void\>


## createSession

▸ `Const` **createSession**(): Promise<void\>

Start a new session

### Returns

Promise<void\>

## getInstance

▸ `Const` **getInstance**(): Instance

Get Grid Session current instance

### Returns

Instance

| Key                 | Type                | Description                                                                                   |
| ------------------- | ------------------- | --------------------------------------------------------------------------------------------- |
| tenantId            | string              | Tenant id in the Grid Console                                                                 |
| sessionId           | string              | Grid Session instance-id                                                                      |
| environment         | string              | Application environment                                                                       |
| dataResidency       | string              | The region where to store the data                                                            |
| country             | string              | Tenant base country (Abbrev.)                                                                 |
| spaceId             | string              | The id of the Space where the device or any entity is located                                 |
| appId               | string              | The id of the gridapp which is running on a device                                            |
| appVersion          | string              | List of Product Type IDs applicable to this product as a reference from ProductTypes Database |
| installationId      | string              | The id of the installation in Grid Console                                                    |
| installationVersion | string              | Build id of the installation                                                                  |
| deviceId            | string \| undefined | Id of the device in the console. If deviceId is not passed, virtual deviceId is created       |
| clientId            | string              | Client id of the requestor. clientId is same as deviceId for registered devices in console    |
| clientCreated       | string              | Date when the client id is created                                                            |
| clientUserAgent     | string              | Requestor user agent                                                                          |
| locationAccuracy    | number \| undefined | Geographic coordinates accuracy                                                               |
| latitude            | number \| undefined | Geographic latitude of the device or requestor                                                |
| longitude           | number \| undefined | Geographic longitude of the device or requestor                                               |
