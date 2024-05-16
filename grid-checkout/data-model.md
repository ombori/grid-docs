# Grid Checkout Data Models

To learn about the definition of each field, check out the [Field Definitions](/grid-checkout/field-definitions) reference guide.

## Transaction

```ts
interface TransactionResponse {
  id: string; // Unique identifier for the transaction.
  tenantId: string; // Identifier of the tenant associated with the transaction.
  status: TransactionStatusEnum; // Status of the transaction.
  items: TransactionItem[]; // Array of items included in the transaction.
  totalAmount: number; // Total amount of the transaction.
  subtotalAmount: number; // Subtotal amount of the transaction before tax and discounts.
  totalTaxAmount: number; // Total tax amount applied to the transaction.
  totalDiscountAmount: number; // Total discount amount applied to the transaction.
  currency: string; // Currency used for the transaction.
  metadata?: unknown; // Additional metadata associated with the transaction (optional).
  createdAt: string; // Timestamp indicating when the transaction was created.
  updatedAt: string; // Timestamp indicating when the transaction was last updated.
  payment?: TransactionPayment; // Information about the payment associated with the transaction (optional).
  customer?: Customer; // Information about the customer associated with the transaction (optional).
}
```

### TransactionItem

```ts
interface TransactionItem {
  productId: string; // Unique identifier of the product.
  name: string; // Name of the product.
  description?: string; // Description of the product (optional).
  unitAmount: number; // Unit amount of the product.
  discountAmount: number; // Discount amount applied to the product.
  subtotalAmount: number; // Subtotal amount of the product.
  totalAmount: number; // Total amount of the product.
  quantity: number; // Quantity of the product.
  taxAmount?: number; // Tax amount applied to the product (optional).
  taxRate?: number; // Tax rate applied to the product (optional).
  metadata?: unknown; // Additional metadata associated with the product (optional).
  alerts?: any[]; // Array of alerts associated with the product.
}
```

### TransactionStatusEnum

```ts
enum TransactionStatusEnum {
  Pending = "pending",
  Success = "success",
  Failed = "failed",
  Cancelled = "cancelled",
}
```

### TransactionPayment

```ts
enum PaymentType {
  StripeOnlineCheckout = "stripeOnlineCheckout",
  Other = "other",
}

interface TransactionOtherPayment {
  type: PaymentType.Other; // Type of payment: 'other'.
  data: any; // Additional payment data.
}

interface TransactionStripeOnlineCheckout {
  type: PaymentType.StripeOnlineCheckout; // Type of payment: 'stripeOnlineCheckout'.
  data: any; // Additional payment data.
}

type TransactionPayment =
  | TransactionOtherPayment
  | TransactionStripeOnlineCheckoutPayment;
```

### Customer

Represents the customer information.

```ts
interface Customer {
  email: string;
}
```

### CheckoutEvent

```ts
enum CheckoutEventType {
  TransactionSuccess = "transaction.success",
  TransactionFailure = "transaction.fail",
}

interface CheckOutEvent {
  data: TransactionResponse;
  type: CheckoutEventType;
}
```
