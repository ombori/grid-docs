# Grid Device Bundles

A Grid Device Bundle is a cutting-edge, flashable image specifically designed for AMD and Giada DN74 architectures. The image contains a GridOS, a robust operating system, and comes with pre-loaded edge applications or Docker images, for seamless and ready-to-deploy edge solutions.

## High Level Overview

  ![](/assets/griddevice-diagram.png ":size=712 :no-zoom")

## Standard Releases
OmboriGrid maintains and releases the standard Grid Device Bundles that can be used in the platform out-of-the-box.

[See device bundles releases](/gridos/releasenotes/)

## Custom Grid Device Bundles
The Grid Device Bundle has a powerful and flexible underlying infrastructure. Third party developers can create custom device bundles and pre-load their custom edge or docker applications which can be used in Factory pre-installations or OEM installations.

### Custom Bundle API Authentication
You can generate an access token from [console](console.omborigrid.com)

### Creating a Custom Bundle
The body should contain below fields.

| Parameter           | Type   | Description                                                                             | Required       |
|---------------------|--------|-----------------------------------------------------------------------------------------|----------------|
| bundleVersion       | string | Based on Semantic Versioning Specification. Example "10.1.0".                           | true           |
| gridos              | string | Based GridOS version. Example ""2.0.5".                                                 | true           |
| deviceArchitectures | array  | "amd64", "dn74". Example ["amd64"].                                                     | true           |
| releaseNotes        | string | Markdown text describing the release notes. Example "New version".                      | true           |
| stage               | string | "qa", "production". Example ["qa"].                                                     | true           |
| customImages        | array  | [customImages Item Parameters](/gridos/device-bundles/?id=customimages-item-parameters) | true           |

#### customImages Item Parameters

| Parameter           | Type   | Description                                                                             | Required |
|---------------------|--------|-----------------------------------------------------------------------------------------|----------|
| url                 | string | Docker image url. Example "omborigridregistry.azurecr.io/ombori.edge:1.8.6"             | true     |
| loginServer         | string | Docker registry login servier                                                           | true     |
| username            | string | Docker registry username                                                                | true     |
| password            | string | Docker registry password                                                                | true     |

#### Example request
```
curl --location --request POST 'https://api.omborigrid.com/api/device-bundle' \
--header 'Authorization: Bearer <TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "bundleVersion": "10.1.3",
    "gridos": "1.5.5",
    "deviceArchitectures": ["amd64"],
    "releaseNotes": "Sample custom image",
    "stage": "qa",
    "images": [
        "omborigridregistry.azurecr.io/ombori.edge:1.8.6",
        "omborigridregistry.azurecr.io/ombori.agent:2.1.5",
        "omborigridregistry.azurecr.io/ombori.screen:3.9.3"
    ],
    "customImages": [
        {
            "url": "vnxedgeappregistry.azurecr.io/test-org-jovanni.vnx-test-iot:0.1.1-amd64",
            "loginServer": "vnxedgeappregistry.azurecr.io",
            "username": "<USERNAME>",
            "password": "<USERNAME>"
        },
        {
            "url": "vnxedgeappregistry.azurecr.io/ombori-test.gate-watch:0.2.4-test1-amd64",
            "loginServer": "vnxedgeappregistry.azurecr.io",
            "username": "<PASSWORD>",
            "password": "<PASSWORD>"
        }
    ]
}

'
```

#### Example response
```
{
  "deviceArchitectures": [
      "amd64"
  ],
  "images": [
    "omborigridregistry.azurecr.io/ombori.edge:1.8.6",
    "omborigridregistry.azurecr.io/ombori.agent:2.1.5",
    "omborigridregistry.azurecr.io/ombori.screen:3.9.3",
    "vnxedgeappregistry.azurecr.io/test-org-jovanni.vnx-test-iot:0.1.1-amd64",
    "vnxedgeappregistry.azurecr.io/ombori-test.gate-watch:0.2.4-test1-amd64"
  ],
  "buildStatus": "processing",
  "bundleVersion": "10.1.4",
  "gridos": "2.0.4",
  "releaseNotes": "Sample custom image",
  "stage": "qa",
  "derivedModules": [
    {
      "_id": "6508a2a89e06bbc1518e3cf3",
      "moduleName": "agent",
      "version": "2.1.5",
      "module": "605cb36d7d02365a44264f36",
      "moduleVersion": "64905b6dce2af0000787918e"
    },
    {
      "_id": "6508a2a89e06bbc1518e3cf4",
      "moduleName": "screen",
      "version": "3.9.3",
      "module": "605cbfa417176c8eabab6452",
      "moduleVersion": "64905b1ace2af00007879144"
    }
  ],
  "createdAt": "2023-09-18T19:19:04.449Z",
  "updatedAt": "2023-09-18T19:19:04.778Z",
  "id": "6508a2a89e06bbc1518e3ced"
}
```

### Getting a Custom Bundle Status


#### Example request

```
curl --location --request GET 'https://api.omborigrid.com/api/device-bundle/<bundle-id>' \
--header 'Authorization: Bearer <TOKEN>'
```

#### Example response

```
{
  "deviceArchitectures": [
      "amd64"
  ],
  "images": [
    "omborigridregistry.azurecr.io/ombori.edge:1.8.6",
    "omborigridregistry.azurecr.io/ombori.agent:2.1.5",
    "omborigridregistry.azurecr.io/ombori.screen:3.9.3",
    "vnxedgeappregistry.azurecr.io/test-org-jovanni.vnx-test-iot:0.1.1-amd64",
    "vnxedgeappregistry.azurecr.io/ombori-test.gate-watch:0.2.4-test1-amd64"
  ],
  "buildStatus": "processing",
  "bundleVersion": "10.1.4",
  "gridos": "2.0.4",
  "releaseNotes": "Sample custom image",
  "stage": "qa",
  "derivedModules": [
    {
      "_id": "6508a2a89e06bbc1518e3cf3",
      "moduleName": "agent",
      "version": "2.1.5",
      "module": "605cb36d7d02365a44264f36",
      "moduleVersion": "64905b6dce2af0000787918e"
    },
    {
      "_id": "6508a2a89e06bbc1518e3cf4",
      "moduleName": "screen",
      "version": "3.9.3",
      "module": "605cbfa417176c8eabab6452",
      "moduleVersion": "64905b1ace2af00007879144"
    }
  ],
  "createdAt": "2023-09-18T19:19:04.449Z",
  "updatedAt": "2023-09-18T19:19:04.778Z",
  "id": "6508a2a89e06bbc1518e3ced"
}
```