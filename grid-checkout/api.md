# Grid Checkout API Reference

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

### [CheckoutEvent] Webhook

When a transaction occurs, our system will send you a response containing detailed information about the transaction. Below is the structure of the data you will receive:

### CheckoutEvent

The [`CheckoutEvent`](/grid-checkout/data-model?id=CheckoutEvent) object represents the event data sent to your webhook URL. It includes the following properties:

- `data`: An object containing information about the transaction.
- `type`: A string indicating the type of checkout event, which can be either `transaction.success` or `transaction.fail`.

### TransactionResponse

The [TransactionResponse](/grid-checkout/data-model?id=Transaction) object contains detailed information about the transaction. It includes the following properties:

- `id`: The unique identifier of the transaction.
- `tenantId`: The identifier of the tenant associated with the transaction.
- `status`: [The status of the transaction](/grid-checkout/data-model?id=TransactionStatusEnum)
- `items`: [An array of objects representing the items included in the transaction](/grid-checkout/data-model?id=TransactionItem).
- `totalAmount`: The total amount of the transaction.
- `subtotalAmount`: The subtotal amount of the transaction before tax and discounts.
- `totalTaxAmount`: The total tax amount applied to the transaction.
- `totalDiscountAmount`: The total discount amount applied to the transaction.
- `currency`: The currency used for the transaction.
- `metadata`: Additional metadata associated with the transaction (optional).
- `createdAt`: The timestamp indicating when the transaction was created.
- `updatedAt`: The timestamp indicating when the transaction was last updated.
- `payment`: [An object containing information about the payment associated with the transaction (optional)](/grid-checkout/data-model?id=TransactionPayment).
- `customer`: [Customer](/grid-checkout/data-model?id=Customer)

### Example Transaction Response

```json
{
  "id": "123456789",
  "tenantId": "abcdef123456",
  "status": "success",
  "items": [
    {
      "name": "Product 1",
      "quantity": 2,
      "price": 10.99
    },
    {
      "name": "Product 2",
      "quantity": 1,
      "price": 15.99
    }
  ],
  "totalAmount": 37.97,
  "subtotalAmount": 37.97,
  "totalTaxAmount": 0,
  "totalDiscountAmount": 0,
  "currency": "USD",
  "createdAt": "2024-05-16T12:00:00Z",
  "updatedAt": "2024-05-16T12:05:00Z",
  "payment": "stripeOnlineCheckout",
  "customer": {
    "email": "john.doe@example.com"
  }
}
```
