# Grid-PIM Data Models

!> Data Model is still in development phase, so there might be breaking changes


To learn about the definition of each field, check out the [Field Definitions](/grid-pim/field-definitions) reference guide.
## GridProduct
```
interface GridProduct {
  ProductId: string;
  Tenant: string;
  Customers?: string[];
  // Main default details
  ProductShortDescription?: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ProductShortDescription: string;
  }>;
  ProductInternalName?: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ProductInternalName: string;
  }>;
  IntroductionDate?: string;
  PlannedAbandonmentDate?: string;
  StorageInstructions?: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    StorageInstructions: string;
  }>;
  ShellLifeDays?: number;
  ConsumerStorageInstruction?: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ConsumerStorageInstruction: string;
  }>;
  ProductShippingInstruction?: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ProductShippingInstruction: string;
  }>;
  
  // Array of translation
  ProductName: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ProductName: string;
  }>;

  // Array of translation
  ProductDescription: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ProductDescription: string;
  }>;

  // Related Products / Recommendations
  RelatedProducts?: Array<{
    RelatedProductId: string;
    ProductRelationshipType: string;
  }>;

  // Variants
  Variants: Array<{
    Id: string; // Item variant Id
    ProductId: string; // Parent product Id
    GlobalTradeItemNumber?: string;
    GtinName?: string;
    EuropeanArticleNumber?: string;
    UniversalProductCode?: string;

    // Item variant name (optional)
    ProductName?: Array<{
      CountryId: string;
      IsoLanguageId: IsoLanguageIds;
      ProductName: string;
    }>;

    PeriodStartDate?: string;
    PeriodEndDate?: string;

    // Added custom field for variants
    Color?: string;
    Style?: string;
    Size?: string;
  }>;

  Brand?: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    BrandName: string;
    BrandDescription?: string;
    BrandMark?: string;
    BrandTrademark?: string;
    BrandLogo?: string;
  }>;

  // Array of translation
  ProductStatus: Array<{
    ProductStatus: ProductStatusEnum;
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    StoreId?: string;
    PeriodStartDate?: string;
    PeriodEndDate?: string;
    ProductStatusNote?: string;
  }>;

  // Equivalent to productDetails in GPF used for filters and data display
  ProductFeature?: Array<{
    Id: string; // SKU or variant Id
    ProductFeatureType: string; // Key of productDetails in GPF
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ProductFeatureValue: string;
  }>;

  // Product Price based on type
  ProductPriceList: Array<{
    Id: string; // SKU or variant Id
    PriceListType: PriceListTypeEnum; // 'Standard' OR 'Promotional'
    StoreId?: string;
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    IsoCurrencyCode: string;
    PricingUomId?: string;
    PeriodStartTimestamp?: string;
    PeriodEndTimestamp?: string;
    SuggestedRetailPrice?: number;
    ListPrice: number;
  }>;

  // Images and links
  CatalogPageLocationProduct: Array<{
    Id: string; // SKU or variant Id
    ProductId: string; // Parent Id
    CatalogType: string; // Ex. "image/png", "video/mp4"
    CatalogPage?: string; // Ex. Root URL of client media site
    CatalogPageLocation?: string; // Ex. Product URL appended to root URL of client page
    CatalogPageLocationProduct: string; // Entire URL value
  }>;

  // Product Type (referenced from ProductType's "ProductTypeId" database)
  ProductType: Array<string>;

  // Product Tags
  ProductLabel?: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ProductLabel: string; // Ex. [Online Exclusive]
  }>;

  // Product Promotion
  ProductPromotion?: {
    PromotionId: string; // Referenced from Promotions Index or an external data (WIP)
    PeriodStartTimestamp?: string;
    PeriodEndTimestamp?: string;
  };

  // Product Quantity
  ProductItemQuantity?: Array<{
    Id: string; // SKU or variant Id
    StoreId?: string;
    ProductItemQuantityStartDate?: string;
    ProductItemQuantityEndDate?: string;
    ProductItemQuantity: number;
  }>;

  ProductVendor?: Array<{
    VendorId: string;
    ProductVendor: string;
    PeriodStartDate?: string;
    PeriodEndDate?: string;
  }>;
}
```

## ProductType
<strong>Note:</strong> 'ProductTypeId' field should be used as value for a product's ProductType field

```
type ProductType = {
  IsRoot: boolean;
  ParentId: string;
  ProductTypeId: string;
  Title: Array<{
    IsoLanguageId: IsoLanguageIds;
    Label: string;
    Path?: string;
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
### LanguageIDs
For Language IDs we use BCP-47 tags, meaning `language-region` structure. Some examples below.
```
enum IsoLanguageIds {
  en_GB = 'en-GB',
  en_US = 'en-US',
  se_SE = 'se-SE',

}
```