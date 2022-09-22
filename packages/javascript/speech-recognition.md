Example:

```js
import SpeechRecognizer from '@ombori/ga-speech-recognition';

const recognizer = new SpeechRecognizer();

  recognizer
    .start({
      language,
      alternativeLanguageCodes,
      contextualPhrases,
      recordingDevice: config.AUDIO_RECORDING_DEVICE || null,
    })
    .subscribe({
      next: onSpeech,
      error: (err: any) => {
        console.error('SPEECH RECOGNIZER ERROR:', err);
        console.info('RESTARTING SPEECH RECOGNIZER');
        setTimeout(() => {
          startRecognizer();
        }, 1000);
      },
    });

  ...
  // Stop
  recognizer.stop();
```