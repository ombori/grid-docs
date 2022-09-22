Example:

```js
import SpeechSynthesizer, { providers, pollyVoiceIds } from '@ombori/ga-speech-synthesis';

const synthesizer = new SpeechSynthesizer({ provider: providers.POLLY });

  synthesizer
    .speakPolly('pleaseEnter', {
      phrase: 'Please enter',
      voiceID: pollyVoiceIds[settings.defaultLanguage as keyof typeof pollyVoiceIds],
    })
    .then(() => {
      if (callback) {
        callback();
      }
    })
    .catch((e) => {
      if (errorPlay) {
        errorPlay();
      }
      console.error(e);
    });
```