# Grid-PIM Integration Flow
To Integrate with Grid Product Information Management, or Grid-PIM, there are several steps you need to follow.

## 1. Setting Up

Setting up with Grid-PIM requires a database initialization. This step is done by Ombori, your Ombori Contact should be able to set this up for you or has already done so.

Once it is set up, you will receive
- tenant-index
- access-key
- Grid-PIM integration URL

## 2. Push Products
You should now start pushing products into the database. There are 2 ways of doing this, either through a backend integration for which you can use our NPM package, or through our API interface.

**Integrate using your backend**

If you want to integrate it in your own backend using our JavaScript npm package, proceed with the [Integration Setup](/grid-pim/integration-flow?id=integration-setup) section of this guide.

**Integrate using APIs**

If you want to integrate using our API from any other system, you can check the [API Reference](/grid-pim/api), we have a Postman collection you can import into [Postman](https://www.postman.com/) and explore the API as well.

To read about how to upload products in the database using our API, check the  [Push Products endpoint](/grid-pim/api?id=post-push-products) in the API reference.

To Read about how to push product types into the database using our API, check the [Push Product Types endpoint](/grid-pim/api?id=post-push-product-types) in the API reference.

?> After downloading the Postman collection, make sure to replace `tenantIndex` and your `accessKey`.

## 3. Integration Setup
Once you start integrating Grid-PIM into other apps, you should use the wrapper package `@ombori/grid-product-service`

This package is hosted on [NPM](https://www.npmjs.com/package/@ombori/grid-product-service)

To install, use npm or yarn

```bash
npm i @ombori/grid-product-service
yarn add @ombori/grid-product-service
```

### Integrate into frontend
To integrate into a front-end application, use `GridProductServiceClient` for readonly operations. Make sure to enter your `tenantIndex` and `accessKey` into the code sample below.

```javascript
import { GridProductServiceClient } from '@ombori/grid-product-service';

const gridpimClient = new GridProductServiceClient({
  tenantIndex: 'test-index',
  accessKey: 'xxx-xxx-xxx',
});

const product = await gridpimClient.getProductById("123456", {
  select: 'ProductId,ProductName'
})

console.log(product);
```

### Integrate into backend
To integrate into a backend application, use `GridProductServiceAdmin` so you can add/remove and update products.

Pushing products into the database is limited, for accurate limitations see the `Push Products` section in the [API reference](/grid-pim/api?id=post-push-products).

 Make sure to enter your `tenantIndex` and `accessKey` into the code sample below.

```javascript
import { GridProductServiceAdmin } from '@ombori/grid-product-service';

const gridpimAdmin = new GridProductServiceAdmin({
  tenantIndex: 'test-index',
  accessKey: 'xxx-xxx-xxx',
});

const idsToRemove = ["ID1", "ID2", "ID3"];

await gridpimAdmin.removeProducts(idsToRemove);
```
