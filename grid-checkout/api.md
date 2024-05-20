# Grid Checkout API Reference (preview)

This is the API reference for Grid Checkout API.

## Base API URL overview

The `{baseUrl}` for the Grid Checkout API is determined by the data residency of your tenant.

`https://api.omborigrid.com/regions/{data-residency}/phycheckout/api/tenants/{tenantId}`

- The `{tenantId}` parameter should be replaced with your actual tenant ID, which is available in your Grid console.
- Please change the value of `<data-residency>` with either `us`, or `uae`.

| Region | URL                                                                         |
| ------ | --------------------------------------------------------------------------- |
| US     | `https://api.omborigrid.com/regions/us/phycheckout/api/tenants/{tenantId}`  |
| UAE    | `https://api.omborigrid.com/regions/uae/phycheckout/api/tenants/{tenantId}` |

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

> **[GET] {base-url}/api/tenants/{tenant-id}/transactions**

Retrieves a list of transactions

#### Response

```
{
    data: Array<Transaction>
}
```

Reference: [Transaction](/grid-checkout/data-model?id=TransactionResponse)
