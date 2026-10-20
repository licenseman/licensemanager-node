
# UpdateLicense


## Properties

Name | Type
------------ | -------------
`expiresAt` | Date
`meta` | { [key: string]: any | null; }
`maxMachines` | number
`maxOfflineDurationSeconds` | number
`maxVersion` | [LicenseMaxVersionInput](LicenseMaxVersionInput.md)
`price` | [PriceInput](PriceInput.md)

## Example

```typescript
import type { UpdateLicense } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "expiresAt": 2027-01-15T09:30:00.000Z,
  "meta": {seats=5},
  "maxMachines": 3,
  "maxOfflineDurationSeconds": 604800,
  "maxVersion": null,
  "price": null,
} satisfies UpdateLicense

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as UpdateLicense
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


