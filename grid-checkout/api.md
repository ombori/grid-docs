# Grid Checkout API Reference (preview)

This is the API reference for Grid Checkout API.

## Base API URL overview

The `{baseUrl}` for the Grid Checkout API is determined by the data residency of your tenant.

| Region | URL                                                  |
| ------ | ---------------------------------------------------- |
| EU     | `https://checkout-v2.eu.omborigrid.net/api/tenants`  |
| US     | `https://checkout-v2.us.omborigrid.net/api/tenants`  |
| UAE    | `https://checkout-v2.uae.omborigrid.net/api/tenants` |

The `{tenantId}` parameter should be replaced with your actual tenant ID, which is available in your Grid console.

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
