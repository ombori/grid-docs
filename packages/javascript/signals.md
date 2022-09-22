This package is used to integrate your nodejs applications with Grid Signals.

Example:

```js
import GridSignals, { types as GridSignalsTypes } from '@ombori/grid-signals';

  const gridSignals = new GridSignals();
  await gridSignals.init(recyclingData.session);

  await Promise.all([
    gridSignals.sendCustomEvent({
      eventType: 'CLAIM_MILES_SUCCESS',
      interaction: true,
      int1: totalMiles,
      int2: recyclingData.totalCount,
    }),
    gridSignals.identifyContact({
      identityType: GridSignalsTypes.IdentityTypeEnum.OTHER,
      customIdentityType: 'etihad',
      interaction: false,
      contact: hashedGuestId,
    }),
    gridSignals.setState({
      key: guestStateKey,
      value: recyclingData.totalCount,
      expiryDuration: 1000 * 60 * 60 * 24 * 365,
    }),
  ]);
```
