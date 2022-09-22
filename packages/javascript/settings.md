This package is used to get the application settings and device properties.

Example:

```js
import { useSettings } from '@ombori/ga-settings';

export default function App() {
  const settings = useSettings<Settings>();

  if (!settings) {
    return <div>Initializing...</div>;
  }

  return <Main settings={settings} /> 
}

```
