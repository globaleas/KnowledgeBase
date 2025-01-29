# EAS Generation

### Generate an EAS alert using EASjs

```javascript
const { generateEASAlert } = require('@globaleas/easjs');

const header = 'ZCZC-CIV-ADR-020173+0100-3441707-ERN/LB-';
generateEASAlert(header)
```

Without any changes to the configuration, it will output the generated SAME alert in the current working directory as
`output.wav`

### Generate an EAS alert with a custom configuration

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
