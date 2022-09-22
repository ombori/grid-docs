This package is used for Edge Module Applications.

Example:

```js
import { connect } from '@ombori/ga-module';
import { Settings } from './schema.js';

const module = await connect<Settings>();

// Show settings that was configured in the console UI
console.log('settings:', module.settings);

// update telemetry
module.updateTelemetry({
  urls: {
    storevue: `http://${DEVICE_NAME}.local:3000/storevue`,
    xovis: `http://${DEVICE_NAME}.local:3000/xovis`,
  },
});
```
