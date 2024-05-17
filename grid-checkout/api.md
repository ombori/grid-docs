# Grid Checkout API Reference

This is the API reference for Grid Checkout integration.

- URL:
  - Please change the values for `<tenant-id>`and `<transaction-id>`
  - Please change the value of `<data-residency>` with either `eu`, `us`, or `uae`.

## URL's overview

The `{base-url}` of the Grid Checkout API depends on the data residency you're working with. Make sure you use the correct URL for the data residency you're working with.

| Region | URL                                                  |
| ------ | ---------------------------------------------------- |
| EU     | `https://checkout-v2.eu.omborigrid.net/api/tenants`  |
| US     | `https://checkout-v2.us.omborigrid.net/api/tenants`  |
| UAE    | `https://checkout-v2.uae.omborigrid.net/api/tenants` |

?> `{tenant-id}` is your tenant id in the grid console.

The following endpoints are available in the API currently.

| Method | Endpoint                                                        | Description                          |
| ------ | --------------------------------------------------------------- | ------------------------------------ |
| GET    | [transaction/{id}](/grid-checkout/api?id=get-transaction-by-id) | Retrieves specific transaction by ID |
| GET    | [transactions](/grid-checkout/api?id=get-transactions)          | Returns list of transactions         |

### [GET] Transaction by ID

> **[GET] {base-url}/api/tenants/{tenant-id}/transactions/{transactionId}**

Retrieves a specific transaction by ID

#### Response

Returns <[`Transaction`](/grid-checkout/data-model?id=transaction)>

#### Query Parameters

To use query parameters, add them as `GET` properties to the `URL`.

| parameter     | type   | Description               | Example  |
| ------------- | ------ | ------------------------- | -------- |
| transactionId | string | The ID of the Transaction | `100001` |

### [GET] Transactions

> **[GET] {base-url}/api/tenants/{tenant-id}/transactions**

Retrieves a list of transactions

#### Response

```
{
    data: Array<Transaction>,
}
```

Reference: [Transaction](/grid-checkout/data-model?id=TransactionResponse)
