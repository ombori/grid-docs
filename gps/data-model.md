# GPS Data Models

!> Data Model is still in development phase, so there might be breaking changes

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
  IntroductionDate?: string; // Start Date (optional) - main date added on RelatedProduct(Variant)
  PlannedAbandonmentDate?: string; // End Date (optional) - main date added on RelatedProduct(Variant)
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
    ProductStatus: ProductStatusEnum; // Ex. Active OR Inactive
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

  // Product categories (Converted semi-colon separated into array)
  ProductType: Array<ProductTypeInterface>; <--- TO BE UPDATED (OCT. 25)

  // Product Tags
  ProductLabel?: Array<{
    CountryId: string;
    IsoLanguageId: IsoLanguageIds;
    ProductLabel: string; // Ex. [Online Exclusive]
  }>;

  // Product Promotion
  ProductPromotion?: {
    PromotionId: string; // Referenced from Promotions Index or external data
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
### Product Type
```
interface ProductTypeInterface {
  Key: string; // Ex. Key1>Key2
  CountryId: string;
  IsoLanguageId: IsoLanguageIds;
  ProductType: string; // Ex. Furniture>Living Room
}
```
### LanguageIDs
```
enum IsoLanguageIds {
  af_ZA = 'af-ZA',
  am_ET = 'am-ET',
  ar_AE = 'ar-AE',
  ar_BH = 'ar-BH',
  ar_DZ = 'ar-DZ',
  ar_EG = 'ar-EG',
  ar_IQ = 'ar-IQ',
  ar_JO = 'ar-JO',
  ar_KW = 'ar-KW',
  ar_LB = 'ar-LB',
  ar_LY = 'ar-LY',
  ar_MA = 'ar-MA',
  ar_OM = 'ar-OM',
  ar_QA = 'ar-QA',
  ar_SA = 'ar-SA',
  ar_SY = 'ar-SY',
  ar_TN = 'ar-TN',
  ar_YE = 'ar-YE',
  as_IN = 'as-IN',
  ba_RU = 'ba-RU',
  be_BY = 'be-BY',
  bg_BG = 'bg-BG',
  bn_BD = 'bn-BD',
  bn_IN = 'bn-IN',
  bo_CN = 'bo-CN',
  br_FR = 'br-FR',
  ca_ES = 'ca-ES',
  co_FR = 'co-FR',
  cs_CZ = 'cs-CZ',
  cy_GB = 'cy-GB',
  da_DK = 'da-DK',
  de_AT = 'de-AT',
  de_CH = 'de-CH',
  de_DE = 'de-DE',
  de_LI = 'de-LI',
  de_LU = 'de-LU',
  dv_MV = 'dv-MV',
  el_GR = 'el-GR',
  en_AU = 'en-AU',
  en_BZ = 'en-BZ',
  en_CA = 'en-CA',
  en_GB = 'en-GB',
  en_IE = 'en-IE',
  en_IN = 'en-IN',
  en_JM = 'en-JM',
  en_MY = 'en-MY',
  en_NZ = 'en-NZ',
  en_PH = 'en-PH',
  en_SG = 'en-SG',
  en_TT = 'en-TT',
  en_US = 'en-US',
  en_ZA = 'en-ZA',
  en_ZW = 'en-ZW',
  es_AR = 'es-AR',
  es_BO = 'es-BO',
  es_CL = 'es-CL',
  es_CO = 'es-CO',
  es_CR = 'es-CR',
  es_DO = 'es-DO',
  es_EC = 'es-EC',
  es_ES = 'es-ES',
  es_GT = 'es-GT',
  es_HN = 'es-HN',
  es_MX = 'es-MX',
  es_NI = 'es-NI',
  es_PA = 'es-PA',
  es_PE = 'es-PE',
  es_PR = 'es-PR',
  es_PY = 'es-PY',
  es_SV = 'es-SV',
  es_US = 'es-US',
  es_UY = 'es-UY',
  es_VE = 'es-VE',
  et_EE = 'et-EE',
  eu_ES = 'eu-ES',
  fa_IR = 'fa-IR',
  fi_FI = 'fi-FI',
  fo_FO = 'fo-FO',
  fr_BE = 'fr-BE',
  fr_CA = 'fr-CA',
  fr_CH = 'fr-CH',
  fr_FR = 'fr-FR',
  fr_LU = 'fr-LU',
  fr_MC = 'fr-MC',
  fy_NL = 'fy-NL',
  ga_IE = 'ga-IE',
  gd_GB = 'gd-GB',
  gl_ES = 'gl-ES',
  gu_IN = 'gu-IN',
  he_IL = 'he-IL',
  hi_IN = 'hi-IN',
  hr_BA = 'hr-BA',
  hr_HR = 'hr-HR',
  hu_HU = 'hu-HU',
  hy_AM = 'hy-AM',
  id_ID = 'id-ID',
  ig_NG = 'ig-NG',
  ii_CN = 'ii-CN',
  is_IS = 'is-IS',
  it_CH = 'it-CH',
  it_IT = 'it-IT',
  ja_JP = 'ja-JP',
  ka_GE = 'ka-GE',
  kk_KZ = 'kk-KZ',
  kl_GL = 'kl-GL',
  km_KH = 'km-KH',
  kn_IN = 'kn-IN',
  ko_KR = 'ko-KR',
  ky_KG = 'ky-KG',
  lb_LU = 'lb-LU',
  lo_LA = 'lo-LA',
  lt_LT = 'lt-LT',
  lv_LV = 'lv-LV',
  mi_NZ = 'mi-NZ',
  mk_MK = 'mk-MK',
  ml_IN = 'ml-IN',
  mn_MN = 'mn-MN',
  mr_IN = 'mr-IN',
  ms_BN = 'ms-BN',
  ms_MY = 'ms-MY',
  mt_MT = 'mt-MT',
  nb_NO = 'nb-NO',
  ne_NP = 'ne-NP',
  nl_BE = 'nl-BE',
  nl_NL = 'nl-NL',
  nn_NO = 'nn-NO',
  oc_FR = 'oc-FR',
  or_IN = 'or-IN',
  pa_IN = 'pa-IN',
  pl_PL = 'pl-PL',
  ps_AF = 'ps-AF',
  pt_BR = 'pt-BR',
  pt_PT = 'pt-PT',
  rm_CH = 'rm-CH',
  ro_RO = 'ro-RO',
  ru_RU = 'ru-RU',
  rw_RW = 'rw-RW',
  sa_IN = 'sa-IN',
  se_FI = 'se-FI',
  se_NO = 'se-NO',
  se_SE = 'se-SE',
  si_LK = 'si-LK',
  sk_SK = 'sk-SK',
  sl_SI = 'sl-SI',
  sq_AL = 'sq-AL',
  sv_FI = 'sv-FI',
  sv_SE = 'sv-SE',
  sw_KE = 'sw-KE',
  ta_IN = 'ta-IN',
  te_IN = 'te-IN',
  th_TH = 'th-TH',
  tk_TM = 'tk-TM',
  tn_ZA = 'tn-ZA',
  tr_TR = 'tr-TR',
  tt_RU = 'tt-RU',
  ug_CN = 'ug-CN',
  uk_UA = 'uk-UA',
  ur_PK = 'ur-PK',
  vi_VN = 'vi-VN',
  wo_SN = 'wo-SN',
  xh_ZA = 'xh-ZA',
  yo_NG = 'yo-NG',
  zh_CN = 'zh-CN',
  zh_HK = 'zh-HK',
  zh_MO = 'zh-MO',
  zh_SG = 'zh-SG',
  zh_TW = 'zh-TW',
  zu_ZA = 'zu-ZA',
}
```

## Field Definitions