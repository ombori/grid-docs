# User Management API

This guide provides detailed documentation on the User Management API available within the OmboriGrid Platform, enabling seamless user management across organizations or tenants.

# Table of Contents

1. [Introduction](#introduction)
2. [Base URL](#base-url)
3. [Authentication](#authentication)
4. [Endpoints](#endpoints)
    - [Create User](#create-user)
    - [Update User Tenant Access](#update-user-tenant-access)
    - [Remove User Tenant Access](#remove-user-tenant-access)
    - [List Tenant Users](#list-tenant-users)

# Introduction

The endpoints in this guide are made available for automation purposes, such as adding users by bulk to the OmboriGrid Platform.

## Base URL

The base URL for all API requests is:

> https://api.omborigrid.com/api

## Authentication

Secure API access requires authentication with a bearer token included in the request header as follows:

Header: { Authorization: `Bearer <token>` }

Tokens can be generated from the Developer tab in the [Grid console](https://console.omborigrid.com).


## Endpoints

### Create User

> **[POST] {base-url}/organizations/{organization-id}/users

Adds a user to a specific organization or tenant


#### Example request
```
curl '{base-url}/organizations/64b8f7c37b256c62fd2e9a61/users' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
    "email": "jovan.axelson@phygrid.com",
    "firstName": "Jovan",
    "lastName": "Axelson",
    "phoneNumber": "+46666666666",
    "roleId": "viewer"
}'
```

#### Example Response
```
{
    "id": "6616acb6c7d190d881076d76",
    "organizationId": "64b8f7c37b256c62fd2e9a61",
    "email": "jovan.axelson@phygrid.com",
    "firstName": "Jovan",
    "lastName": "Axelson",
    "phoneNumber": "+46666666666",
    "roleId": "viewer"
}
```

#### Body parameters

| Parameter       | Type   | Description                                                                             | Example                     | Required |
|-----------------|--------|-----------------------------------------------------------------------------------------|-----------------------------|----------|
| email           | string | User email address used for login                                                       | jovan.axelson@phygrid.com   | true     |
| roleId          | string | "admin", "editor", "viewer", or `<custom-user-role-id>`                                 | viewer                      | true     |
| firstName       | string | First name of the user                                                                  | Jovan                       | false    |
| lastName        | string | Last name of the user                                                                   | Axelson                     | false    |
| phoneNumber     | string | Phone number of the user                                                                | +46666666666                | false    |
| password        | string | Optional default password of the user. User can reset the password after it is added.   | A12ldl3s4g!                 | false    |

- *Password requirements*
  - At least one uppercase letter
  - At least one lowercase letter
  - At least one special character (#?!@$.%^&*-)
  - At least ten characters
- *Custom User Role ID*
  - The ability to see and copy the custom user role ID from the console will be coming soon.

### Update User Tenant Access

> **[PUT] {base-url}/organizations/{organization-id}/users/{user-id}

Updates a user role to a specific tenant

#### Example request
```
curl --request PUT '{base-url}/organizations/64b8f7c37b256c62fd2e9a61/users/6616acb6c7d190d881076d76' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
  "roleId": "admin"
}'
```

#### Example Response
```
{
    "id": "6616acb6c7d190d881076d76",
    "organizationId": "64b8f7c37b256c62fd2e9a61",
    "email": "jovan.axelson@phygrid.com",
    "firstName": "Jovan",
    "lastName": "Axelson",
    "phoneNumber": "+46666666666",
    "roleId": "admin"
}
```

#### Body parameters

| Parameter       | Type   | Description                                                                             | Example                     | Required |
|-----------------|--------|-----------------------------------------------------------------------------------------|-----------------------------|----------|
| roleId          | string | "admin", "editor", "viewer", or `<custom-user-role-id>`                                 | viewer                      | true     |

- *Custom User Role ID*
  - The ability to see and copy the custom user role ID from the console will be coming soon.

### Remove User Tenant Access

> **[DELETE] {base-url}/organizations/{organization-id}/users/{user-id}

Removes a user access from a specific tenant

#### Example request
```
curl --request DELETE '{base-url}/organizations/64b8f7c37b256c62fd2e9a61/users/6616acb6c7d190d881076d76' \
--header 'Authorization: Bearer <token>'
```

#### Example Response
```
http_status: 200

{
  "message": "Successfully removed the user from the tenant"
}
```

### List Tenant Users

> **[GET] {base-url}/organizations/{organization-id}/users

Lists users in a specific tenant

#### Example request
```
curl '{base-url}/organizations/5d08a21ae6abf5150035a734/users?page=1&limit=5' \
--header 'Authorization: Bearer <token>'
```

#### Example Response
```
{
    "docs": [
        {
          "id": "6616acb6c7d190d881076d76",
          "organizationId": "64b8f7c37b256c62fd2e9a61",
          "email": "jovan.axelson@phygrid.com",
          "firstName": "Jovan",
          "lastName": "Axelson",
          "phoneNumber": "+46666666666",
          "roleId": "admin"
        }
        {
            "id": "6119f5eb166d1d33846e112b",
            "organizationId": "64b8f7c37b256c62fd2e9a61",
            "email": "alpha.tuna.705@phygrid.com",
            "firstName": "Alpha",
            "lastName": "Tuna",
            "phoneNumber": "+639170000000",
            "roleId": "viewer"
        }
    ],
    "totalDocs": 2,
    "limit": 5,
    "hasPrevPage": false,
    "hasNextPage": false,
    "page": 1,
    "totalPages": 1,
    "pagingCounter": 1,
    "prevPage": null,
    "nextPage": null
}
```

#### Query parameters

| Parameter       | Type   | Description                                                                             | Example                     | Required |
|-----------------|--------|-----------------------------------------------------------------------------------------|-----------------------------|----------|
| page            | number | Default is 1. Pagination page of the tenant users list                                  | 1                           | false    |
| limit           | number | Default is 50. Pagination limit of the tenant users list                                | 5                           | false    |
