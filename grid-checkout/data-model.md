# Grid Checkout Data Models

## Transaction

The Transaction model serves as the core data structure within Grid Checkout, central to processing and managing transactions efficiently.

### Field Definitions

This document provides definitions for all fields outlined in the Grid Checkout Transaction data model. It details nested structures under separate headings for clarity and organization.

| Field               | Description                                                                                                                                | Example                                                                     |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| id                  | A unique Grid Checkout identifier for the transaction.                                                                                     | 123456                                                                      |
| status              | Indicates the current status of the transaction, represented by a value from the `TransactionStatusEnum`.                                  | [TransactionStatusEnum](/grid-checkout/data-model?id=transactionStatusEnum) |
| items               | An array containing documents representing individual items included in the transaction (`TransactionItem`).                                | [TransactionItem](/grid-checkout/data-model?id=TransactionItem)             |
| totalAmount         | The total amount of the transaction, including taxes, discounts and shipping, in cents, represented as an integer.                         | 880                                                                         |
| subtotalAmount      | The subtotal amount of the transaction, excluding taxes and discounts, in cents, represented as an integer.                                | 800                                                                         |
| totalTaxAmount      | The total tax amount applied to the transaction, in cents, represented as an integer.                                                       | 160                                                                         |
| totalDiscountAmount | The total discount amount applied to the transaction, in cents, represented as an integer.                                                  | 80                                                                          |
| totalShippingAmount | The total shipping cost amount, in cents, represented as an integer.                                                                       | 80                                                                          |
| currency            | The currency used for monetary values in the transaction, represented as a string.                                                         | USD                                                                         |
| metadata            | Additional metadata associated with the transaction, if available.                                                                         | {}                                                                          |
| createdAt           | The date and time when the transaction was created, represented as a string.                                                               | `2024-05-16T10:54:42.005Z`                                                  |
| updatedAt           | The date and time when the transaction was last updated, represented as a string.                                                          | `2024-05-16T10:54:42.005Z`                                                  |
| payment             | Details about the payment associated with the transaction, if available, represented by a `TransactionPayment`.                            | [TransactionPayment](/grid-checkout/data-model?id=transactionPayment)       |
| customer            | Information about the `customer` associated with the transaction, represented by a Customer object.                                        | [Customer](/grid-checkout/data-model?id=customer)                           |
| shipping            | Information about the `shipping` associated with the transaction, represented by a Shipping object.                                        | [Shipping](/grid-checkout/data-model?id=shipping)                           |

### Type Definitions Reference

#### TransactionResponse

```js
interface TransactionResponse {
  id: string;
  tenantId: string; 
  spaceId: string;
  status: TransactionStatusEnum; 
  items: TransactionItem[]; 
  totalAmount: number; 
  subtotalAmount: number;
  totalTaxAmount: number; 
  totalDiscountAmount: number; 
  totalShippingAmount: number; 
  currency: string; 
  metadata?: unknown; 
  createdAt: string; 
  updatedAt: string;
  payment?: TransactionPayment;
  customer?: Customer; 
  shipping?: Shipping;
}
```

#### TransactionItem

```js
interface TransactionItem {
  productId: string; 
  name: string; 
  description?: string; 
  unitAmount: number; 
  discountAmount: number; 
  subtotalAmount: number; 
  totalAmount: number;
  quantity: number; 
  taxAmount?: number; 
  taxRate?: number; 
  metadata?: unknown; 
}
```

#### TransactionStatusEnum

```js
enum TransactionStatusEnum {
  Pending = "pending",
  Success = "success",
  Failed = "failed",
  Cancelled = "cancelled",
}
```

#### TransactionPayment

```js
enum PaymentType {
  StripeOnlineCheckout = "stripeOnlineCheckout",
  Other = "other",
}

interface TransactionOtherPayment {
  type: PaymentType.Other;
  amount: number;
  data: any;
}

interface TransactionStripeOnlineCheckout {
  type: PaymentType.StripeOnlineCheckout; 
  amount: number;
  data: TransactionStripeOnlineCheckoutData; 
}

interface TransactionStripeOnlineCheckoutData {
  shippingRateId?: string;
  clientReferenceId: string;
  checkoutSessionId: string;
  paymentIntentId: string;
  amountTotal: number;
  amountSubtotal: number;
  currency: string;
  customerDetails: {
    billingAddress: {
      city: string,
      country: string,
      line1: string,
      line2?: string,
      postalCode: string,
      state: string,
    };
  };
  totalDetails: {
    amountDiscount: number;
    amountShipping: number;
    amountTax: number;
  };
  status: string;
}

type TransactionPayment =
  | TransactionOtherPayment
  | TransactionStripeOnlineCheckoutPayment;
```

#### Customer

Represents the customer information.

```js
interface Customer {
  email: string;
  name: string;
  phone: string;
}
```

#### Shipping

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
