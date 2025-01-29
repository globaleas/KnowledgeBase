# SAME Decoding

### Decode a SAME header using EASjs
```javascript
const { decodeSame } = require('@globaleas/easjs')

const result = decodeSame('ZCZC-WXR-TSW-006081-006013-006001-006087-006085+0100-3401900-WJON/BLU-')
console.log(result)
```

#### Output:

```javascript
{
  organization: 'The National Weather Service has issued ',
  event: 'Tsunami Warning',
  locations: 'San Mateo, CA; Contra Costa, CA; Alameda, CA; Santa Cruz, CA; Santa Clara, CA',
  timing: { start: '7:00 PM on December 6', end: '8:00 PM on December 6' },
  sender: 'WJON/BLU',
  formatted: 'The National Weather Service has issued a Tsunami Warning for San Mateo, CA; Contra Costa, CA; Alameda, CA; Santa Cruz, CA; Santa Clara, CA; beginning at 7:00 PM on December 6 and ending at 8:00 PM on December 6. Message from WJON/BLU'
}
```

### Grab a specific value from the decoded data

```javascript
const { decodeSame } = require('@globaleas/easjs')

### To grab a specific value from the decoded data:

const result = decodeSame('ZCZC-WXR-TSW-006081-006013-006001-006087-006085+0100-3401900-WJON/BLU-')
console.log(result.organization)
```

#### Output: {id="output_1"}

```
The National Weather Service has issued
```

### Only translate an event code

```javascript
const { eventTranslator } = require('@globaleas/easjs')

const result = eventTranslator('TSW')
console.log(result)
```

#### Output: {id="output_2"}

```
Tsunami Warning
```

### Translate a FIPS code

```javascript
const { translateFips } = require('@globaleas/easjs')

const result = translateFips('006081')
console.log(result)
```

#### Output: {id="output_3"}

```javascript
{
  subdivision: 'All',
  county: 'San Mateo',
  region: 'CA',
  formatted: 'All San Mateo, CA'
}
```

### Translate an originator

```javascript
const { origTranslator } = require('@globaleas/easjs')

const result = origTranslator('PEP')
console.log(result)
```

#### Output: {id="output_4"}

```
United States Government
```
