# Integrating Grid Signals on your Websites

!> Grid Signals is currently in pre-release. Breaking changes are not likely but can still occur before production release in March

This page describes how you can integrate your existing or new websites to Grid Signals.

## Step 1: Install Web Signals
Go to the [Grid Console](https://omborigrid.com), and navigate to the Marketplace page. Install the Web Signals app.

![](https://media.omborigrid.com/media/5cbac8a388e174147b878cdd/e3d26af0-7eae-11ec-bec9-4dcd0899bd02 ":size=600 :no-zoom")

![](https://media.omborigrid.com/media/5cbac8a388e174147b878cdd/a0e4c800-7eae-11ec-bec9-4dcd0899bd02 ":size=600:no-zoom")

## Step 2: Configure your app
Copy the script from the console `Settings` to your index.html

![](https://media.omborigrid.com/media/5cbac8a388e174147b878cdd/70f12070-7eaf-11ec-bec9-4dcd0899bd02 ":size=600:no-zoom")

Example:

```js
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <meta
      name="description"
      content="Web site created using create-react-app"
    />
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
    <title>React App</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <script async src="https://app.omborigrid.com/web-signals/signal.js"></script>
    <script>
      window.gridDataLayer = window.gridDataLayer || [];
      function gridSignal(){gridDataLayer.push(arguments);}
      gridSignal('init', 'tenantId', 'XXXXXX');
      gridSignal('init', 'installationId', 'XXXXXX');
      gridSignal('init', 'spaceId', 'XXXXXX');
      gridSignal('init', 'dataResidency', 'EU');
      gridSignal('init', 'country', 'SE');
    </script>
    <div id="root"></div>
  </body>
</html>
```

## Step 3: Send events
On page load, the Web Signals will be initialized.

To send events, use `gridSignal('<function-name>', <args>)` function in your app.

See [Event Tracking](grid-signals/tracking-events) page for the list of available functions.

```js
...
  gridSignal('sendCartAdd', {
    productId: 'XXXXXX',
    quantity: 1
  });
...
```

## Step 4: Real-time dashboards

Real-time dashboards are available in the [Grid Console](https://console.omborigrid.com)
