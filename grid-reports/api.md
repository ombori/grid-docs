# Grid reports API Reference

This is the API reference for Grid reports.

## Postman Collection
For easy configuration and testing, here's a Postman collection you can import into Postman.

?> Download the [Postman Collection](/grid-reports/grid-reports.postman-collection.json)

### Variables

| Variable          | Description                                                                          |
|-------------------|--------------------------------------------------------------------------------------|
| `access-token`    | An access token that you can generate in Grid Console, under the "Developer" tab.    |
| `base-url`        | Depends on the data residency you're working with. Check the "base-url" table below. |
| `tenant-id`       | Your tenant id in the grid console.                                                  |
| `installation-id` | Your installation id in the grid console.                                            |
| `space-id`        | Your space id in the grid console.                                                   |
| `device-id`       | Your device id in the grid console.                                                  |
| `app-id`          | Your app id in the grid console.                                                     |

## Request authentication
- In Grid Console, you need to generate an Access Token under the "Developer" tab.
- Add `Authorization: Bearer <token>` in the request header, with the generated access token value.

## URL's overview

The `{base-url}` of the Grid reports API depends on the data residency you're working with. Make sure you use the correct URL for the data residency you're working with.

| Region | URL                                              |
| ------ | ------------------------------------------------ |
| EU     | `https://api.omborigrid.com/regions/eu/reports`  |
| US     | `https://api.omborigrid.com/regions/us/reports`  |
| IN     | `https://api.omborigrid.com/regions/in/reports`  |
| AU     | `https://api.omborigrid.com/regions/au/reports`  |
| UAE    | `https://api.omborigrid.com/regions/uae/reports` |

The current API implements 5 dimensions for reports:

- [Tenant reports](/grid-reports/tenant-reports)
- [Installation reports](/grid-reports/installation-reports)
- [Space reports](/grid-reports/space-reports)
- [Device reports](/grid-reports/device-reports)
- [App reports](/grid-reports/app-reports)
