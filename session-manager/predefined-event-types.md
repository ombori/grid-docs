# Predefined Event Types
The session manager supports a number of predefined event types. These are used to define the structure of the session object when you want to use these standard event types.

This list contains a list of predefined event types, group by usage.

## Generic Events
The Generic Events are intended for generic purposes that can apply in many situations.

- App Start
- Content View
- Search
- Search Clear
- Rating

### App Start

```json
{
    eventType: "APP_START"
}
```

## Contact Event Types
The Contact Event Types are defined to identify your users and to fetch or create contacts for them.

- Identify a person as a contact
- Send contact metadata
- Send detected mood (from computer vision)
- Send detected age (from computer vision)
- Send detected gender (from computer vision)

### Identify a person as a contact

```json
{
    eventType: "CONTACT_IDENTIFY",
    str1: "PHONE",
    str2: "0123456780
}
```

The definition of this field is as follows:

| parameter | required | description                                                                       |
| --------- | -------- | --------------------------------------------------------------------------------- |
| str1      | ✅        | The type of contact detail. Possible values are: `PHONE`, `EMAIL` and `CLIENT_ID` |
| str2      | ✅        | The value of the contact detail                                                   |

## Ecommerce Event Types
The Ecommeerce Event Types are defined for interacting with your shop.

- Category View
- Product View
- Fashion Look View
- Add to Cart
- View Cart
- Remove from Cart
- Clear Cart
- Go to Checkout
- Purchase

