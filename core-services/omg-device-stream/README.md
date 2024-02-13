# Grid Device Stream API

Grid Device Stream API allows secured remote access to the device through API requests.

## Base URL

https://device-streams.{data-residency}.omborigrid.net

Data residency options:
- eu
- uae
- au
- us
- in

## Authentication

Header: { Authorization: `Bearer <token>` }

You can create a token from the Developer tab in [Grid console](console.omborigrid.com).

## Endpoints

There is currently one endpoint available for this service and will be extended later on.


### [POST] Start a tunnel link session

> **[POST] {base-url}/tunnel/{device-name}/{ip-address}/{port}

Returns a tunnel session link

#### Example request
```
curl -X POST 'https://device-streams.eu.omborigrid.net/tunnel/my-device/192.168.30.24/80' \
-H 'Authorization: Bearer <token>'
```

#### Response
```
{
  "tunnel": string;
}
```

#### Query parameters
To use query parameters, add them as `GET` properties to the `URL`.

| Parameter       | Type   | Description                                                                             | Example      | Required |
|-----------------|--------|-----------------------------------------------------------------------------------------|--------------|----------|
| device-name     | string | The device name assigned in console                                                     | my-device    | true     |
| ip-address      | string | Defines the IP address of the server that you want to connect through the device        | 192.168.1.30 | true     |
| port            | number | Port of the server that you want to connect through the device                          | 80           | false    |

