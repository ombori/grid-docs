This package is used to integrate your react application with grid signals.

Example:

```js
import { useGridSignals, getInstance as gs } from '@ombori/grid-signals-react';

const Init = ({ settings, sessionId }: { settings: Settings; sessionId: string }) => {
  const isReady = useGridSignals({
    sessionId,
    tenantId: '60ca1d7d8aee1300067753d0',
    environment: 'PROD',
    spaceId: '1234d979ce0cbb6d30c92c13',
  });

  return isReady
    ? <SessionScreen settings={settings} sessionId={sessionId} />
    : <LoadingScreen />;
}

const SessionScreen = () => {
  useEffect(() => {
    gs().createSession();
  }, []);

  return <div>Session Loaded</div>;
}
```