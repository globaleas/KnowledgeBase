# EAS Generation

### Generate an EAS alert using EASjs

```javascript
const { generateEASAlert } = require('@globaleas/easjs');

const header = 'ZCZC-CIV-ADR-020173+0100-3441707-ERN/LB-';
generateEASAlert(header)
```

Without any changes to the configuration, it will output the generated alert in the current working directory as
`output.wav`

#### Generate an EAS alert with a custom configuration

```javascript
// Import the MODES object for configuration
const { generateEASAlert, MODES } = require('@globaleas/easjs');

const header = 'ZCZC-CIV-ADR-020173+0100-3441707-ERN/LB-';
generateEASAlert(header, {
    audioPath: 'alert-audio.mp3',
    filename: 'final-alert.wav',
    format: 'wav',
    mode: MODES.DIGITAL
})
```

This will output the generated alert as `final-alert.wav` in the current working directory.

#### Custom Parameters for Generation

- `audioPath` - The path to the audio file to use for the alert audio message.
  - *EASjs currently supports mp3 and wav files*
- `filename` - The name of the output file
- `format` - The format of the output file (wav or mp3)
- `mode` - The mode of the alert:
    - `MODES.DEFAULT` - Style similar to a Digital Alert Systems DASDEC
    - `MODES.DIGITAL` - Style similar to a SAGE Digital ENDEC
    - `MODES.TRILITHIC` - Style similar to Trilithic EASy ENDECs
    - `MODES.NWS` - Similar to `MODES.DEFAULT` but with a 1050 Hz attention tone