# Grid Alerts - Notification Groups

A Notification group defines the action to take when one of the alert rule's conditions is met.

  ![](/assets/notification-groups-list.png ":size=512 :no-zoom")

## Creating or updating a Notification Group

  ![](/assets/notification-group-form.png ":size=512 :no-zoom")

### Name
The name of the Notification Group

### Description
The description of the Notification Group

### Email recipients
The list of users who will receive email notifications

  ![](/assets/notification-group-form-email-recipients.png ":size=512 :no-zoom")

### Webhook URL
The URL endpoint which is called when one of the alert rule's conditions is met.

## Device Status Change Alert Webhook

### Type
```
interface WebhookDeviceAlertStatusEnum {
  OFFLINE = 'OFFLINE',
  ONLINE = 'ONLINE',
  FAILING = 'FAILING'
}

interface WebookDeviceStatusAlertItem {
  "deviceName": string;
  "link": string;
  "statusLastUpdateTime": string;
  "env": string;
  "appId": string;
  "spaceId": string;
  "uuid": string;
  "values":{
      "statusLastUpdateTime": string;
      "diffFromCurrentTimeInMin": number;
      "status": WebhookDeviceAlertStatusEnum; 
      "ruleDuration": number;
  }
}

interface WebhookDeviceStatusAlertTenant {
  [tenantId: string]: {
    tenantName: string;
    devices: WebookDeviceAlertItem[];
  }
}

interface WebhookDeviceStatusAlertBody {
  ruleConditionType: "device-status";
  subject: string;
  url: string;
  tenants: WebhookDeviceAlertTenant; 
}
```

### Example
```
{
  "ruleConditionType":"device-status",
  "subject":"[Critical] Device Status",
  "url":"https://api-qa.omborigrid.com/regions/qa/alerts/v1/webhook-test",
  "tenants":{
      "5f2b2a4728292736dbf414c4":{
        "tenantName":"Jovanni's Workspace",
        "devices":[
            {
              "deviceName":"vnx1",
              "link":"https://console-qa.omborigrid.com/organisations/5f2b2a4728292736dbf414c4/devices/v3/752391bd-76ec-4697-ab76-7bd8836e7794/screen/",
              "statusLastUpdateTime":"2023-08-10T10:30:00.581Z",
              "env":"prod",
              "appId":"64d4b9619b73b9000798f1ae",
              "spaceId":"63b465f7a953630008cab162",
              "uuid":"752391bd-76ec-4697-ab76-7bd8836e7794",
              "values":{
                  "statusLastUpdateTime":"2023-08-10T10:30:00.581Z",
                  "diffFromCurrentTimeInMin":230746,
                  "status":"OFFLINE",
                  "ruleDuration":5
              }
            },
            {
              "deviceName":"abcd123",
              "link":"https://console-qa.omborigrid.com/organisations/5f2b2a4728292736dbf414c4/devices/v3/5c4b5af6-e843-4185-af9c-fd949ac83572/screen/",
              "statusLastUpdateTime":"2023-01-31T07:29:17.554Z",
              "env":"prod",
              "appId":"6419dda44b135b0008b04a3a",
              "spaceId":"63b465f7a953630008cab162",
              "uuid":"5c4b5af6-e843-4185-af9c-fd949ac83572",
              "values":{
                  "statusLastUpdateTime":"2023-01-31T07:29:17.554Z",
                  "diffFromCurrentTimeInMin":505966,
                  "status":"OFFLINE",
                  "ruleDuration":5
              }
            }
        ]
      }
  }
}
```

## Device Sessions Count Alert Webhook

### Type
```
interface WebookDeviceSessionCountAlertItem {
  "deviceName": string;
  "link": string;
  "statusLastUpdateTime": string;
  "env": string;
  "appId": string;
  "spaceId": string;
  "uuid": string;
  "values":{
      "count": number;
      "date": string;
  }
}

interface WebhookDeviceSessionCountAlertTenant {
  [tenantId: string]: {
    tenantName: string;
    devices: WebookDeviceAlertItem[];
  }
}

interface WebhookDeviceSessionCountAlertBody {
  ruleConditionType: "device-analytics-session-count";
  subject: string;
  url: string;
  tenants: WebhookDeviceSessionCountAlertTenant;
}
```

### Example
```
{
  "ruleConditionType":"device-analytics-session-count",
  "subject":"[Critical] Device Analytics Session Count",
  "url":"https://api-qa.omborigrid.com/regions/qa/alerts/v1/webhook-test",
  "tenants":{
      "5f2b2a4728292736dbf414c4":{
        "tenantName":"Jovanni's Workspace",
        "devices":[
            {
              "deviceName":"vnx1",
              "link":"https://console-qa.omborigrid.com/organisations/5f2b2a4728292736dbf414c4/devices/v3/752391bd-76ec-4697-ab76-7bd8836e7794/screen/",
              "statusLastUpdateTime":"2023-08-10T10:30:00.581Z",
              "env":"prod",
              "appId":"64d4b9619b73b9000798f1ae",
              "spaceId":"63b465f7a953630008cab162",
              "uuid":"752391bd-76ec-4697-ab76-7bd8836e7794",
              "values":{
                  "count":0,
                  "date":"2024-01-16"
              }
            },
            {
              "deviceName":"abcd123",
              "link":"https://console-qa.omborigrid.com/organisations/5f2b2a4728292736dbf414c4/devices/v3/5c4b5af6-e843-4185-af9c-fd949ac83572/screen/",
              "statusLastUpdateTime":"2023-01-31T07:29:17.554Z",
              "env":"prod",
              "appId":"6419dda44b135b0008b04a3a",
              "spaceId":"63b465f7a953630008cab162",
              "uuid":"5c4b5af6-e843-4185-af9c-fd949ac83572",
              "values":{
                  "count":0,
                  "date":"2024-01-16"
              }
            }
        ]
      }
  }
}
```