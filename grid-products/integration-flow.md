# Grid Products Integration Flow
To Integrate with Grid Products, there are several steps you need to follow.

## 1. Prerequisite

You need to make sure that you have an account in the Ombori Grid Console.

You'll need the following information:
1. Your tenant id in Grid Console
2. Any Environment id that you have defined in the Grid Console (e.g. prod)
3. Access Token
  - You need to generate an Access Token under "Developers" tab to be used later on for every request
     - [Products API](/grid-pim/api?id=request-authentication)
     - [Spaces API](/grid-pim/spaces-api?id=request-authentication)

## 2. Push Spaces

This step is applicable if you want your data to be visible only to a specific store / location for example.

To Read about how to create spaces into the database using our API, check the [Create Space endpoint](/grid-pim/api?id=post-space) in the API reference.

The returned `id` value will be used as values for `spaces` and `spaceId` fields later on when you format your product data into the [GridProduct](/grid-pim/data-model?id=gridproduct) format

## 3. Push ProductTypes

The next step would be to push your product categories or product types that will be used later on for the `productType` field of your products.

Specific example for ProductTypes usage is for the category navigation in Endless Aisle application.

To Read about how to push product types into the database using our API, check the [Push Product Types endpoint](/grid-pim/api?id=post-push-product-types) in the API reference.


## 4. Push Products
You should now start pushing products into the database. There are 2 ways of doing this, either through a backend integration for which you can use our NPM package or through our API interface.

**Integrate using your backend**

If you want to integrate it in your own backend using our JavaScript npm package, proceed with the [Integration Setup](/grid-products/integration-flow?id=integration-setup) section of this guide.

**Integrate using APIs**

If you want to integrate using our API from any other system, you can check the [API Reference](/grid-products/api), we have a Postman collection you can import into [Postman](https://www.postman.com/) and explore the API as well.

To read about how to upload products in the database using our API, check the  [Push Products endpoint](/grid-products/api?id=post-push-products) in the API reference.

?> After downloading the Postman collection, make sure to replace `tenant-id` and `environment` value and set the request Header's `x-api-key` with your generated access token in Grid Console.

## 5. Integration Setup
Once you start integrating Grid Products into other apps, you should use the wrapper package `@ombori/grid-products`

This package is hosted on [NPM](https://www.npmjs.com/package/@ombori/grid-products)

To install, use npm or yarn

```bash
npm i @ombori/grid-products
yarn add @ombori/grid-products
```

### Integrate into frontend
To integrate into a front-end application, use `GridProductServiceClient` for read-only operations. Make sure to enter your `tenantId`, `environment`, and `accessToken` into the code sample below.

```javascript
import { GridProductServiceClient } from '@ombori/grid-products';

const gridProductClient = new GridProductServiceClient({
  tenantId: 'test',
  environment: 'staging',
  accessToken: 'xxx-xxx-xxx',
});

const product = await gridpimClient.getProductById("123456", {
  select: 'productId,productName'
})

console.log(product);
```

### Integrate into backend
To integrate into a backend application, use `GridProductServiceAdmin` so you can add/remove and update products.

Pushing products into the database is limited, for accurate limitations see the `Push Products` section in the [API reference](/grid-products/api?id=post-push-products).

 Make sure to enter your `tenantId`, `environment`, and `accessToken` into the code sample below.

```javascript
import { GridProductServiceAdmin } from '@ombori/grid-products';

const gridProductAdmin = new GridProductServiceAdmin({
  tenantId: 'test-index',
  environment: 'staging',
  accessToken: 'xxx-xxx-xxx',
});

const idsToRemove = ["ID1", "ID2", "ID3"];

await gridpimAdmin.removeProducts(idsToRemove);
```