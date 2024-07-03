# Webhooks overview

Webhooks provide a powerful mechanism to enhance the integration of Phygrid's checkout solutions with your existing systems. This feature facilitates seamless interactions with fulfillment systems, customer relationship management (CRM) software, and similar platforms, optimizing operational efficiency and data synchronization.

## Configuring webhooks

Since the Grid Checkout API is currently in preview, please note that this section will be updated soon. Future enhancements will include an API for configuring webhooks and a user interface in the Grid Console for setting up webhook destination URLs.

## Webhooks

### [CheckoutEvent] Webhook

A webhook for a checkout event is triggered upon the completion of a transaction.

#### CheckoutEvent

The [`CheckoutEvent`](/grid-checkout/data-model?id=CheckoutEvent) object represents the event data sent to your webhook URL. It includes the following properties:

- `data`: [An object containing information about the transaction](/grid-checkout/data-model?id=Transaction).
- `type`: A string indicating the type of checkout event, which can be either `transaction.success` or `transaction.fail`.

#### Example Checkout Event

```json
{
  "type": "transaction.success",
  "data": {
    "id": "xxxxxxxxxxxx",
    "status": "success",
    "items": [
      {
        "productId": "123",
        "description": "Product Description",
        "name": "Product Name",
        "quantity": 2,
        "unitAmount": 200,
        "taxRate": 0.1,
        "taxAmount": 40,
        "discountAmount": 0,
        "subtotalAmount": 400,
        "totalAmount": 440,
        "metadata": {},
        "alerts": [],
        "customProperties": {
          "internalId": "123456"
        }
      },
      {
        "productId": "124",
        "description": "Product Description",
        "name": "Product Name",
        "quantity": 2,
        "unitAmount": 200,
        "taxRate": 0.1,
        "taxAmount": 40,
        "discountAmount": 0,
        "subtotalAmount": 400,
        "totalAmount": 440,
        "metadata": {},
        "alerts": [],
        "customProperties": {
          "internalId": "123456"
        }
      }
    ],
    "tenantId": "xxxxxxxxxxxxxxxx",
    "spaceId": "1234",
    "totalAmount": 890,
    "subtotalAmount": 880,
    "totalTaxAmount": 0,
    "totalDiscountAmount": 0,
    "totalShippingAmount": 10,
    "customer": {
      "phone": "111-1111-1111",
      "name": "xyz",
      "email": "xyz@phygrid.com"
    },
    "shipping": {
      "address": {
        "city": "city",
        "country": "country",
        "line1": "line1",
        "line2": "line2",
        "postalCode": "postalCode",
        "state": "state"
      },
      "rate": {
        "amount": 100,
        "name": "Fedex"
      }
    },
    "currency": "USD",
    "payment": {
      "type": "stripeOnlineCheckout",
      "amount": 100,
      "data": {
        "lastPaymentError": "",
        "shippingAddress": {},
        "shippingRateid": "",
        "checkoutSessionId": "xxxxxxxxxxxxxxxxxxxx",
        "paymentIntentId": "xxxxxxxxxxxxxxxxxxxx",
        "amountTotal": "",
        "amountSubtotal": "",
        "currency": "",
        "customerDetails": "",
        "status": "",
        "totalDetails": ""
      }
    },
    "createdAt": "2024-05-17T10:10:30.513Z",
    "updatedAt": "2024-05-17T10:11:15.510Z"
  }
}
```
