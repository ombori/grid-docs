# Grid Products Data Models

!> Data Model is still in the development phase, so there might be breaking changes, which will be announced when you're actively using Grid Products, and in the 


To learn about the definition of each field, check out the [Field Definitions](/grid-products/field-definitions) reference guide.
## GridProduct
```
interface GridProduct {
  productId: string;
  // spaceIds will hold the list of spaceIds where item is visible
  spaceIds?: Array<string>;
  productShortDescription?: Array<{
    isoLanguageId: IsoLanguageIds;
    productShortDescription: string;
  }>;
  productInternalName?: Array<{
    isoLanguageId: IsoLanguageIds;
    productInternalName: string;
  }>;
  introductionDate?: string;
  plannedAbandonmentDate?: string;
  storageInstructions?: Array<{
    isoLanguageId: IsoLanguageIds;
    storageInstructions: string;
  }>;
  shellLifeDays?: number;
  consumerStorageInstruction?: Array<{
    isoLanguageId: IsoLanguageIds;
    consumerStorageInstruction: string;
  }>;
  productShippingInstruction?: Array<{
    isoLanguageId: IsoLanguageIds;
    productShippingInstruction: string;
  }>;
  productName: Array<{
    isoLanguageId: IsoLanguageIds;
    productName: string;
  }>;
  productDescription: Array<{
    isoLanguageId: IsoLanguageIds;
    productDescription: string;
  }>;
  relatedProducts?: Array<{
    relatedProductId: string;
    productRelationshipType: ProductRelationshipTypes;
  }>;

  // Variants
  variants: Array<{
    id: string; // Item variant Id
    productId: string; // Parent product Id
    globalTradeItemNumber?: Array<string>;
    gtinName?: Array<string>;
    europeanArticleNumber?: Array<string>;
    universalProductCode?: Array<string>;

    // Item variant name (optional)
    productName?: Array<{
      isoLanguageId: IsoLanguageIds;
      productName: string;
    }>;

    periodStartDate?: string;
    periodEndDate?: string;

    color?: string;
    style?: string;
    size?: string;
  }>;

  brand?: Array<{
    isoLanguageId: IsoLanguageIds;
    brandName: string;
    brandDescription?: string;
    brandMark?: string;
    brandTrademark?: string;
    brandLogo?: string;
  }>;

  productStatus: Array<{
    productStatus: ProductStatusEnum;
    isoLanguageId: IsoLanguageIds;
    spaceId: string;
    periodStartDate?: string;
    periodEndDate?: string;
    productStatusNote?: string;
  }>;

  productFeature?: Array<{
    id: string; // Variant Id
    isoLanguageId: IsoLanguageIds;
    productFeatureType: string;
    productFeatureValue: string;
  }>;

  // Product Price based on type (Standard or Promotional)
  productPriceList: Array<{
    id: string; // Variant Id
    priceListType: PriceListTypeEnum; // 'Standard' OR 'Promotional'
    listPrice: number;
    spaceId: string;
    isoLanguageId: IsoLanguageIds;
    isoCurrencyCode: string;
    pricingUomId?: string;
    periodStartTimestamp?: string;
    periodEndTimestamp?: string;
    suggestedRetailPrice?: number;
  }>;

  // Images
  catalogPageLocationProduct: Array<{
    id: string; // Variant Id
    productId: string;
    catalogType: string; // Ex. "image/png", "video/mp4"
    catalogPage?: string; // Ex. Root URL of client media site
    catalogPageLocation?: string; // Ex. Product URL appended to root URL of client page
    catalogPageLocationProduct: string; // Entire URL value
  }>;

  // Product Type (referenced from ProductType's "ProductTypeId" database)
  productType: Array<string>;

  // Product Labels - displayed like stickers
  productLabel?: Array<{
    isoLanguageId: IsoLanguageIds;
    productLabel: string; // Ex. [Online Exclusive]
  }>;

  // Product Tags to increase searchability of a product
  productTags?: Array<{
    isoLanguageId: IsoLanguageIds;
    productTags: Array<string>;
  }>

  // Product Quantity per variant
  productItemQuantity?: Array<{
    id: string; // Variant Id
    spaceId: string;
    productItemQuantityStartDate?: string;
    productItemQuantityEndDate?: string;
    productItemQuantity: number;
  }>;

  productVendor?: Array<{
    vendorId: string;
    productVendor: string;
    periodStartDate?: string;
    periodEndDate?: string;
  }>;
}
```

## ProductType
<strong>Note:</strong> 'ProductTypeId' field should be used as value for a product's ProductType field

```
type ProductType = {
  isRoot: boolean;
  parentId: string;
  productTypeId: string;
  title: Array<{
    isoLanguageId: IsoLanguageIds;
    label: string;
    path?: string;
  }>;
};
```

## Enums and Interfaces

### PriceListType
```
enum PriceListTypeEnum {
  Standard = 'Standard',
  Promotional = 'Promotional',
}
```

### ProductStatus
```
enum ProductStatusEnum {
  Active = 'Active',
  Inactive = 'Inactive',
  Discontinued = 'Discontinued',
  Dormant = 'Dormant',
  Frozen = 'Frozen',
  Replaced = 'Replaced',
  Obsolete = 'Obsolete',
  Abandoned = 'Abandoned',
  Blocked = 'Blocked',
}
```

### ProductRelationshipTypes
```
enum ProductRelationshipTypes {
    Recommended = "Recommended"
}
```

### LanguageIDs
For Language IDs we use BCP-47 tags, meaning `language-region` structure. Some examples below.
```
enum IsoLanguageIds {
  en_GB = 'en-GB',
  en_US = 'en-US',
  se_SE = 'se-SE',

}
```

### Space

```
type Space = {
  {
    id: string; // auto-generated
    organizationId: string;
    displayName: string;
    type: 'location' | 'section' | 'custom'; // defaults to location
    longitude: number;
    latitude: number;
    notes?: string;
    externalId: string;
  },
}
```