# Grid Reports Library

This library helps to build schema for analytics reports.

## Installation

`npm i @ombori/grid-reports --save` or `yarn add @ombori/grid-reports`

## Example

```
import {
  AnalyticsSchema,
  CardType,
  SessionInteractionType,
} from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        { type: CardType.Sessions, interactionType: SessionInteractionType.Interactive },
      ],
    },
  ],
};

export default analyticsSchema;
```

As a result of the above example, you will get an analytics report with one card that shows information about user sessions.

![Example](https://ams03pap001files.storage.live.com/y4mxe38c0M8Mt4-rGoCoKj-DbuLeiyeT8wr_a5LidZgBrDmoG0hC6zS8NFIhvE1Z204qzniAx0-wNrDmBfoeIN3bzkL9oSH-uxvEADwPHTOEmbsn6Xn8cOCyQytlh4S56wYvbSLVzLW_VfroOYJU4xgmWtuqx3sDpaSYjEWahz5xxL7SE16LXhFlNujTNU6XAqA?width=2442&height=1430&cropmode=none)

Analytics schema is an object that should match AnalyticsSchema type. Do not forget to export your schema using default export.

## Description

There are several types that helps you to build analytics schema.

### AnalyticsSchema

`import { AnalyticsSchema } from '@ombori/grid-reports';`

> Top level type for your analytics schema.

```
import { AnalyticsSchema } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {};

export default analyticsSchema;
```

**Options**

- `groups: object[]`
  - **Required**
  - List of groups for this analytics report.

### Group

> Analytics report consists of groups of reports. Each group defines its own list of report cards. If you have a big analytics report with a lot of data it maybe handy to split data into several groups.

```
import { AnalyticsSchema } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [],
    },
  ],
};

export default analyticsSchema;
```

Property `groups` defines a list of analytics report groups. 

One group has next options.

**Options**

- `name: string`
    - **Required**
    - Defines report group name.
- `cards: object[]`
    - **Required**
    - List of cards for this report group. 
- `columnsCount: number`
    - **Optional**
    - Defines number of columns for report group layout.
- `gridStyles: object`
    - **Optional**
    - It is possible to customize report group layout with grid-* css properties. For example, gridStyles: { 'grid-gap': '20px' }.

### Card

> Each report group has its own list of analytics cards.

```
import { AnalyticsSchema, CardType, SessionInteractionType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        {
          type: CardType.Sessions,
          interactionType: SessionInteractionType.Interactive,
        }
      ],
    },
  ],
};

export default analyticsSchema;
```

## Cards

Each card is an object with a certain type and card specific properties.

### Sessions card

> Adds card with data about user sessions to the report group.

```
import { AnalyticsSchema, CardType, SessionInteractionType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        {
          type: CardType.Sessions,
          interactionType: SessionInteractionType.Interactive,
        }
      ],
    },
  ],
};

export default analyticsSchema;
```

**Options**

- `type: CardType.Sessions`
    - **Required**
- `interactionType: SessionInteractionType`
    - **Optional**
    - Defines the type of sessions data to be shown. Use SessionInteractionType enum.
- `gridStyles: object`
    - **Optional**
    - It is possible to customize card layout with grid-* css properties.

![Sessions card](https://ams03pap001files.storage.live.com/y4mI5TbY6t37sugI9uGQiDqSkaVTVOb1STm1xOvnPVDj4VFIN87Pomx6a_YBFnhuAPA8xMysryZKMJ8VkkbCTAjxIneO5P-_s0KFTsyLAT30Hg-D6HLhOK1LV1XY6cn5qGhBNNe1TrusY66Om-Z7pbN-k4k2TQAN6vFBpTWAdyJL1qOsDjC1VIiv5__HSCwA7MU?width=1108&height=686&cropmode=none)

### Nps card

> Adds card with data about NPS score and number of nps replies.

```
import { AnalyticsSchema, CardType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        { type: CardType.Nps }
      ],
    },
  ],
};

export default analyticsSchema;
```

**Options**

- `type: CardType.Nps`
  - **Required**
- `gridStyles: object`
  - **Optional**
  - It is possible to customize card layout with grid-* css properties.

![NPS card](https://ams03pap001files.storage.live.com/y4my7y3gwBuYGYOybHzVwHp_uabNKSdiH_IK9RTQgR85e57QKIehcVc4gIEvkHLWr5z6CF3ZQZFB8utG24enYoRDEhBQizJDgTWWOA_kgieqhP9FMQA7BuD718NmaSXbw-mzJJZ1h8fXPBQGySDuCAODTpiq7bF97GaspbxQrnfs6ev9QA9euc2abw2FgXd7gTp?width=1106&height=578&cropmode=none)

### EventsList card

> Adds card with list of captured events.

```
import { AnalyticsSchema, CardType, InteractionType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        { type: CardType.EventsList, interactionType: InteractionType.Interactive },
      ],
    },
  ],
};

export default analyticsSchema;
```

**Options**

- `type: CardType.EventsList`
  - **Required**
- `interactionType: InteractionType`
  - **Optional**
  - Defines the type of events data to be shown. Use InteractionType enum.
- `gridStyles: object`
  - **Optional**
  - It is possible to customize card layout with grid-* css properties.

![Events list card](https://ams03pap001files.storage.live.com/y4mAJFQEl1_ZEIGdfFQ695_G52U_4KsMLL0mrqMm1BEKNWcgxD-xXiPkGPVyZ0UwsF3Bx3MYZtFlCYRv4lQoBVtsmfRTXJeLrfjwM6mTnhMPuWX5J3jmLLUQDF2AprtBf77LpS-_K0EHWyL01d6s1PnbQqujahsDIo9XJYbzdf7fHsCWYzO4EHMmB_A8tUYAhv_?width=1108&height=968&cropmode=none)

### EventsFunnel card

> Adds card with events funnel based on predefined list of events.

```
import { AnalyticsSchema, CardType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        {
          type: CardType.EventsFunnel,
          title: 'Sales conversions funnel',
          events: ['CATEGORY_VIEW', 'PRODUCT_VIEW', 'CART_ADD', 'CHECKOUT', 'PURCHASE'],
        },
      ],
    },
  ],
};

export default analyticsSchema;
```

**Options**

- `type: CardType.EventsFunnel`
  - **Required**
- `title: string`
  - **Required**
  - Defines card title.
- `events: string[]`
  - **Required**
  - Defines list of events that should be used to build events funnel. For example, ['CATEGORY_VIEW', 'PRODUCT_VIEW', 'CART_ADD', 'CHECKOUT', 'PURCHASE'].
- `gridStyles: object`
  - **Optional**
  - It is possible to customize card layout with grid-* css properties.

![Events funnel card](https://ams03pap001files.storage.live.com/y4m-i_XI-PS_pdetauG7XTEW55I6RSe5aOOufmJTWh-dVElgY4ecggQpg8MP9OdXHEf8ID0qQYbOUpFvRUaKVZUiZ16FcTnBRCVSOrQy2muCUS_NJ_9FlKfz2w4GKE3ys5K0WpQqdmbptwl9Whs6Wk3qnKtSr2sRLAGxarbFnb2WSVkTwje4nRXg7kIw4z5VCbQ?width=1108&height=972&cropmode=none)

### ProductsEventCount card

> Adds card with list of captured product events.

```
import { AnalyticsSchema, CardType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        {
          type: CardType.ProductsEventCount,
          eventType: 'PRODUCT_VIEW',
          title: 'Product views',
        },
      ],
    },
  ],
};

export default analyticsSchema;
```

**Options**

- `type: CardType.ProductsEventCount`
  - **Required**
- `title: string`
  - **Required**
  - Defines card title.
- `eventType: string`
  - **Required**
  - Defines an event type.
- `gridStyles: object`
  - **Optional**
  - It is possible to customize card layout with grid-* css properties.

![Products event count card](https://ams03pap001files.storage.live.com/y4mnhiCKUIPiJy-ZVkuVoYTESCFzsk9CZxOG0arQOlAm4RstwkLtNhv_iMNcj9H7RYDgOmUdCTuX30vMqNHv8CaxYQvIkLSvUz5hDKdnWSbICOajHhlDZBbHXRR4Ml1yeWJaZ2kulyn-JxS1ftbapvsGdYtujWMh0w-xFOQ64j9mn2Cg3fkHSQ_yhm3BA3ONF7N?width=1120&height=642&cropmode=none)

### CategoriesEventCount card

> Adds card with list of captured product categories events.

```
import { AnalyticsSchema, CardType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        { type: CardType.CategoriesEventCount },
      ],
    },
  ],
};

export default analyticsSchema;
```

**Options**

- `type: CardType.CategoriesEventCount`
  - **Required**
- `gridStyles: object`
  - **Optional**
  - It is possible to customize card layout with grid-* css properties.

![Categories event count card](https://ams03pap001files.storage.live.com/y4mPL956hcbWXLGkygsct2knVAlgjUz425zNdDsqj-CFg-9cTmK0g-dJ9se4KS0K8mhT_B9NtAKGWinMZu22AHDJ6Tmi-RK5JormlIw0h_kqKeY7cxH_Dnc22J9yCL6b2w-C9RB6vqCtYeRbV3HEQI97r1t0FlSkSkfXVV_qspHQnjqmJJoC6Qw9rT_hBLBsYtn?width=1112&height=636&cropmode=none)

### EventsFlow card

> Adds card that shows flow of captured events.

```
import { AnalyticsSchema, CardType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        { type: CardType.EventsFlow }
      ],
    },
  ],
};

export default analyticsSchema;
```

**Options**

- `type: CardType.EventsFlow`
  - **Required**
- `gridStyles: object`
  - **Optional**
  - It is possible to customize card layout with grid-* css properties.

![Events flow card](https://ams03pap001files.storage.live.com/y4muCRn0ovjexIO89MUJ6GZxa4CxVRGLFfjI6dEwhU9OpLePrmUusBITyRF_XAE2UOD_ynojH_pH7nNqumIJVcPB7E1t31Lo-MEdM4xb4F8WHxHiAdG7Nwf8-KaTevgt2ikrmr669BavK4PT98LuAwdPhAdQ0cJoM3GmhLML1iOaKTUwP8s-a4lvZ-T36x5POiL?width=2260&height=1224&cropmode=none)

### WeekHeatmap card

> Adds card with sessions or events data that is shown as a heatmap.

```
import { AnalyticsSchema, CardType } from '@ombori/grid-reports';

const analyticsSchema: AnalyticsSchema = {
  groups: [
    {
      name: 'Overview',
      cards: [
        {
          type: CardType.WeekHeatmap,
          title: 'Sessions week heatmap',
          dataSource: {
            type: WeekHeatmapDataSourceType.Sessions,
            interactionType: SessionInteractionType.Interactive,
          },
        },
      ],
    },
  ],
};

export default analyticsSchema;
```

- `type: CardType.WeekHeatmap`
  - **Required**
- `title: string`
  - **Required**
  - Defines card title.
- `dataSource: WeekHeatmapDataSourceSessions | WeekHeatmapDataSourceEvents`
  - **Required**
  - `WeekHeatmapDataSourceSessions: { type, interactionType }`
    - `type: WeekHeatmapDataSourceType.Sessions`
      - **Required**
    - `interactionType: SessionInteractionType`
      - **Optional**
  - `WeekHeatmapDataSourceEvents: { type, eventType }`
    - `type: WeekHeatmapDataSourceType.Events`
      - **Required**
    - `eventType: string`
      - **Required**
      - Defines the specific event type to be used as data source. For example, CART_ADD.
- `gridStyles: object`
  - **Optional**
  - It is possible to customize card layout with grid-* css properties.

![Week heatmap card](https://ams03pap001files.storage.live.com/y4m5GBexNv6WNrCSvX--6IVMGDAaRMysfbf-INzOPMdMpmbi5PhvFszc7NJD3IIW8Te83sjjywID5811YpR0RLsXUKJI99IMKJre2IaPZKIE4VSjS0gTm5ip7gWASQH879Gz2PcZXKyPj_kwzPy13xXby82Pb7qfz7TylPc_GLBMb74JuIH95lEDZXKKUp9K7_0?width=2348&height=1334&cropmode=none)
