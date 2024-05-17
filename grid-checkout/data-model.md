# Grid Checkout Data Models

# Field Definitions

This document contains the definition of all fields mentioned in the Grid Checkout Transaction data-model document.

Nested structures are indicated by separate headers.

| Field               | Description                                                                                                                               | Example                                                                     |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| id                  | A unique identifier for the transaction.                                                                                                  | 123456                                                                      |
| status              | Indicates the current status of the transaction, represented by a value from the `TransactionStatusEnum`.                                 | [TransactionStatusEnum](/grid-checkout/data-model?id=transactionStatusEnum) |
| items               | An array containing documents representing individual items included in the transaction (`TransactionItem`).                              | [TransactionItem](/grid-checkout/data-model?id=TransactionItem)             |
| totalAmount         | The total amount of the transaction, including taxes and discounts, represented as a number.                                              | 880                                                                         |
| subtotalAmount      | The subtotal amount of the transaction, excluding taxes and discounts, represented as a number.                                           | 800                                                                         |
| totalTaxAmount      | The total tax amount applied to the transaction, represented as a number.                                                                 | 160                                                                         |
| totalDiscountAmount | The total discount amount applied to the transaction, represented as a number.                                                            | 80                                                                          |
| currency            | The currency used for monetary values in the transaction, represented as a string.                                                        | USD                                                                         |
| metadata            | Additional metadata associated with the transaction, if available. The type is `unknown`, indicating flexibility in the data structure.ID | {}                                                                          |
| createdAt           | The date and time when the transaction was created, represented as a string.                                                              | `2024-05-16T10:54:42.005Z`                                                  |
| updatedAt           | The date and time when the transaction was last updated, represented as a string.                                                         | `2024-05-16T10:54:42.005Z`                                                  |
| payment             | Details about the payment associated with the transaction, if available, represented by a `TransactionPayment`. ID                        | [TransactionPayment](/grid-checkout/data-model?id=transactionPayment)       |
| customer            | Information about the `customer` associated with the transaction, represented by a Customer object.                                       | [Customer](/grid-checkout/data-model?id=customer)                           |
| shipping            | Information about the `shipping` associated with the transaction, represented by a Shipping object.                                       | [Shipping](/grid-checkout/data-model?id=shipping)                           |

## Transaction

```js
interface TransactionResponse {
  id: string; // Unique identifier for the transaction.
  tenantId: string; // Identifier of the tenant associated with the transaction.
  spaceId: string; // Identifier of the space/organization associated with the transaction.
  status: TransactionStatusEnum; // Status of the transaction.
  items: TransactionItem[]; // Array of items included in the transaction.
  totalAmount: number; // Total amount of the transaction.
  subtotalAmount: number; // Subtotal amount of the transaction before tax and discounts.
  totalTaxAmount: number; // Total tax amount applied to the transaction.
  totalDiscountAmount: number; // Total discount amount applied to the transaction.
  totalShippingAmount: number; // Total shipping amount applied to the transaction.
  currency: string; // Currency used for the transaction.
  metadata?: unknown; // Additional metadata associated with the transaction (optional).
  createdAt: string; // Timestamp indicating when the transaction was created.
  updatedAt: string; // Timestamp indicating when the transaction was last updated.
  payment?: TransactionPayment; // Information about the payment associated with the transaction (optional).
  customer?: Customer; // Information about the customer associated with the transaction (optional).
  shipping?: Shipping;
}
```

## TransactionItem

```js
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
}
```

## TransactionStatusEnum

```js
enum TransactionStatusEnum {
  Pending = "pending",
  Success = "success",
  Failed = "failed",
  Cancelled = "cancelled",
}
```

## TransactionPayment

```js
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

## Customer

Represents the customer information.

```js
interface Customer {
  email: string;
  name: string;
  phone: string;
}
```

## Shipping

```js
interface Shipping {
  address: {
    city: string,
    country: string,
    line1: string,
    line2?: string,
    postalCode: string,
    state: string,
  };
  rate: {
    amount: number,
    name: string,
  };
}
```

## CheckoutEvent

```js
enum CheckoutEventType {
  TransactionSuccess = "transaction.success",
  TransactionFailure = "transaction.fail",
}

interface CheckOutEvent {
  data: TransactionResponse;
  type: CheckoutEventType;
}
```
