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
