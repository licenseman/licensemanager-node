
# Customer


## Properties

Name | Type
------------ | -------------
`id` | string
`productId` | string
`email` | string
`name` | string
`licenseCount` | number
`stripeCustomerId` | string
`createdAt` | Date

## Example

```typescript
import type { Customer } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": c9Wd3RtE,
  "productId": x7Kp2QaZ,
  "email": jane@example.com,
  "name": Jane Doe,
  "licenseCount": 3,
  "stripeCustomerId": cus_NffrFeUfNV2Hib,
  "createdAt": 2026-01-15T09:30:00.000Z,
} satisfies Customer

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Customer
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


