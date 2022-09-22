This package is used to render QR Codes with shortened urls and analytics tracking. Under the hood, it's integrated with grid signals.

Example:

```js
import ShortUrlQrCode from '@ombori/ga-react-qr-run';

...
  <ShortUrlQrCode
    url="https://omborigrid.com"
    size={32}
  >
    {(shortUrl) => (
      <ShortUrlContainer>
        <ShortUrl>{shortUrl.replace(/^https:\/\//, '')}</ShortUrl>
      </ShortUrlContainer>
    )}
  </ShortUrlQrCode>
...
```
