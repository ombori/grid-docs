# Grid Checkout API Reference (preview)

This is the API reference for Grid Checkout API.

## Request authentication

- In Grid Console, you need to generate an Access Token under the "Developer" tab.
- Add `x-api-key` in the request header, with the generated access token value.

## Base API URL overview

The `{baseUrl}` for the Grid Checkout API is determined by the data residency of your tenant.

Regional Grid Checkout base API URLs:

| Region | URL                                                  |
| ------ | ---------------------------------------------------- |
| EU     | `https://api.omborigrid.com/regions/eu/phycheckout`  |
| US     | `https://api.omborigrid.com/regions/us/phycheckout`  |
| UAE    | `https://api.omborigrid.com/regions/uae/phycheckout` |
| IN     | `https://api.omborigrid.com/regions/in/phycheckout`  |
| AU     | `https://api.omborigrid.com/regions/au/phycheckout`  |

- The standard base URL for most API operations is structured as follows: `https://api.omborigrid.com/regions/{dataResidency}/phycheckout/api/tenants/{tenantId}`

- The `{tenantId}` parameter should be substituted with your specific tenant ID, which can be found in your Grid console.

The following endpoints are available in the API:

| Method | Endpoint                                                        | Description                          |
| ------ | --------------------------------------------------------------- | ------------------------------------ |
| GET    | [transaction/{id}](/grid-checkout/api?id=get-transaction-by-id) | Retrieves specific transaction by ID |
| GET    | [transactions](/grid-checkout/api?id=get-transactions)          | Returns list of transactions         |

### [GET] Transaction by ID

> **[GET] {baseUrl}/api/tenants/{tenantId}/transactions/{transactionId}**

Retrieves a specific transaction by ID

#### Response

```
{
    data: Transaction
}
```

Reference: [Transaction](/grid-checkout/data-model?id=TransactionResponse)

#### Query Parameters

| parameter     | type   | Description               | Example  |
| ------------- | ------ | ------------------------- | -------- |
| transactionId | string | The ID of the Transaction | `100001` |

### [GET] Transactions

> **[GET] {baseUrl}/api/tenants/{tenantId}/transactions**

Retrieves a list of transactions based on specified query parameters.

#### Query Parameters

To use query parameters, add them as `GET` properties to the `URL`.

| parameter | type   | Description                                            | Example |
| --------- | ------ | ------------------------------------------------------ | ------- |
| limit     | number | Maximum number of item count to retrieve `Default: 50` | `100`   |
| page      | number | Current pagination result `Default: 1  `               | `1`     |

#### Response

```
{
    items: Array<Transaction>,
    page: number,
    totalPages: number,
    totalItems: number,
    limit: number,
}
```

Reference: [Transaction](/grid-checkout/data-model?id=TransactionResponse)
