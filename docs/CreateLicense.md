
# CreateLicense


## Properties

Name | Type
------------ | -------------
`email` | string
`key` | string
`policyId` | string
`expiresAt` | Date
`meta` | { [key: string]: any | null; }
`maxMachines` | number
`maxOfflineDurationSeconds` | number
`price` | [PriceInput](PriceInput.md)
`maxVersion` | [LicenseMaxVersionInput](LicenseMaxVersionInput.md)
`sendKey` | boolean

## Example

```typescript
import type { CreateLicense } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "email": jane@example.com,
  "key": 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF,
  "policyId": p4Rt8LmQ,
  "expiresAt": 2027-01-15T09:30:00.000Z,
  "meta": {seats=5},
  "maxMachines": 3,
  "maxOfflineDurationSeconds": 604800,
  "price": null,
  "maxVersion": null,
  "sendKey": true,
} satisfies CreateLicense

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateLicense
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


