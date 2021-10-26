# GPS Integration Flow
To Integrate with Grid Product Service, or GPS, there are several steps you need to follow.

## 1. Setting Up

Setting up with GPS requires an database initialisation. This step is done by Ombori, your Ombori Contact should be able to set this up for you or has already done so.

Once it is set up, you will receive
- tenant-index
- access-key
- GPS integration URL

## 2. Push Products
You should now start pushing products into the database, read about this in the [API reference](/gps/api?id=post-push-products). This will populate the database based on your input. 

## 3. Push Product Types
You can also push product types into the database, read about this in the [API reference](/gps/api?id=post-push-product-types). This will populate the product types database that can be referenced to a product's ProductType value.

## 4. Integration Setup
Once you start integrating GPS into other apps, you should use the wrapper package `@ombori/grid-product-service`

This package is hosted on [NPM](https://www.npmjs.com/package/@ombori/grid-product-service)

To install, use npm or yarn

```bash
npm i @ombori/grid-product-service
yarn add @ombori/grid-product-service
```

### Integrate into frontend
To integrate into a front-end application, use `GridProductServiceClient` for readonly operations.

```javascript
import { GridProductServiceClient } from '@ombori/grid-product-service';

const gpsClient = new GridProductServiceClient({
  tenantIndex: 'test-index',
  accessKey: 'xxx-xxx-xxx',
});

const product = await gpsClient.getProductById("123456", {
  select: 'ProductId,ProductName'
})

console.log(product);
```

### Integrate into backend
To integrate into a backend application, use `GridProductServiceAdmin` so you can add/remove and update products.

Pushing products into the database is limited, for accurate limitations see the `Push Products` section in the [API reference](/gps/api?id=post-push-products).

```javascript
import { GridProductServiceAdmin } from '@ombori/grid-product-service';

const gpsAdmin = new GridProductServiceAdmin({
  tenantIndex: 'test-index',
  accessKey: 'xxx-xxx-xxx',
});

const idsToRemove = ["ID1", "ID2", "ID3"];

await gpsClient.removeProducts(idsToRemove);
```