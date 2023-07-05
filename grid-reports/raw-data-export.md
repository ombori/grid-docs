# Raw Data Export

You can export a tenant's raw analytics data from the OmboriGrid Platform through the Data Export feature.

There are two (2) options:
1. Export through the console. Go to your tenant in [console.omborigrid.com](console.omborigrid.com), and navigate to `Menu > Data export`.
2. Export through API

## Exporting through API
- Below is the instruction on you can export a tenant's raw analytics data.

### Request authentication
- In [Grid Console](console.omborigrid.com), you need to generate an Access Token under the "Developer" tab.
- Add `Authorization: Bearer <token>` in the request header, with the generated access token value.

### Creating an export job
#### Endpoint
| Method | URL                                                                |
| ------ | ---------------------------------------------------------          |
|  POST  | `https://api.omborigrid.com/api/analytics-export-job`              |

#### Body
| Key               | Description                                                                          |
|-------------------|--------------------------------------------------------------------------------------|
| `tenantId`        | Tenant ID                                                                            |
| `dataDateFrom`    | Data date from in `YYYY-MM-DD` format                                                |
| `dataDateTo`      | Data date to in `YYYY-MM-DD` format                                                  |

#### Response
| Key               | Description                                                                          |
|-------------------|--------------------------------------------------------------------------------------|
| `status`          | [queued,  processing, done]                                                           |
| `id`              | Job ID                                                                               |
| `tenantId`        | Tenant ID                                                                            |
| `jobExpiryDate`   | Date when the job will be archived.                                                  |
| `dataDateFrom`    | Start date range of the data included in the exported parquet files                  |
| `dataDateTo`      | End date range of the data included in the exported parquet files                    |
| `createdAt`       | Date when the job was created                                                        |
| `updatedAt`       | Date when the job was updated                                                        |
| `filename `       | The target filename of the export job output                                         |

### Getting an export job status
| Method | URL                                                                |
| ------ | ---------------------------------------------------------          |
|  GET   | `https://api.omborigrid.com/api/analytics-export-job/<job-id>`     |

#### Response
| Key               | Description                                                                          |
|-------------------|--------------------------------------------------------------------------------------|
| `status`          | [queued, processing, done]                                                           |
| `id`              | Job ID                                                                               |
| `tenantId`        | Tenant ID                                                                            |
| `jobExpiryDate`   | Date when the job will be archived.                                                  |
| `dataDateFrom`    | Start date range of the data included in the exported parquet files                  |
| `dataDateTo`      | End date range of the data included in the exported parquet files                    |
| `createdAt`       | Date when the job was created                                                        |
| `updatedAt`       | Date when the job was updated                                                        |
| `filename `       | The target filename of the export job output                                         |
| `downloadUrl `    | Export job output's download url                                                     |
| `fileSize    `    | Export job output's file size                                                        |
