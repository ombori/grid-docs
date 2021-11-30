# Grid Session APIs

When integrating Grid Session Manager on server side, you may want to just directly send events to the Grid Session API.

- [sendClient](/session-manager/session-api?id=sendclient)
- [sendSession](/session-manager/session-api?id=sendsession)
- [sendEvent](/session-manager/session-api?id=sendevent)

## sendClient

▸ `Const` **sendClient**(`client`): Promise<void\>

Send device client information

### Parameters

| Key | Type | Required |
| :------ | :------ | :------ |
| `tenantId` | string | yes | 
| `clientId` | string | yes |
| `clientCreated` | string | yes |
| `clientUserAgent` | number | yes |
| `dataResidency` | string | yes |
| `country` | string | yes |
| `locationAccuracy` | number | no |
| `latitude` | number | no |
| `longitude` | number | no |
| `clientScreenWidth` | number | no |
| `clientScreenHeight` | number | no |
| `clientScreenColorDepth` | number | no |
| `clientScreenPixelDepth` | number | no |

### Returns

Promise<void\>



## sendSession

▸ `Const` **sendSession**(`session`): Promise<void\>

Start or create a session

### Parameters

| Key | Type | Required |
| :------ | :------ | :------ |
| `tenantId` | string | yes | 
| `sessionId` | string | yes |
| `sessionCreated` | string | yes |
| `environment` | number | yes |
| `dataResidency` | string | yes |
| `country` | string | yes |
| `spaceId` | string | yes |
| `appId` | string | yes |
| `appVersion` | string | yes |
| `installationId` | string | yes |
| `installationVersion` | string | yes |
| `deviceId` | string | yes |
| `clientId` | string | yes |
| `locationAccuracy` | number | no |
| `latitude` | number | no |
| `longitude` | number | no |

### Returns

Promise<void\>

## sendEvent

▸ `Const` **sendEvent**(`event`): Promise<void\>

Track session events

### Parameters

| Key | Type | Required |
| :------ | :------ | :------ |
| `tenantId` | string | yes | 
| `eventTime` | string | yes |
| `dataResidency` | string | yes |
| `sessionId` | number | yes |
| `clientId` | string | yes |
| `eventType` | string | yes |
| `interaction` | boolean | no |
| `productId` | string | no |
| `categoryId` | string | no |
| `int1` | number | no |
| `int2` | number | no |
| `int3` | number | no |
| `int4` | number | no |
| `int5` | number | no |
| `str1` | string | no |
| `str2` | string | no |
| `str3` | string | no |
| `str4` | string | no |
| `str5` | string | no |
### Returns

Promise<void\>
