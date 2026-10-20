
# License


## Properties

Name | Type
------------ | -------------
`id` | string
`productId` | string
`policyId` | string
`customerId` | string
`key` | string
`createdAt` | Date
`expiresAt` | Date
`meta` | { [key: string]: any | null; }
`stripePaymentIntentId` | string
`maxMachines` | number
`maxOfflineDurationSeconds` | number
`activeMachineCount` | number
`lastActivatedAt` | Date
`maxVersion` | [LicenseMaxVersion](LicenseMaxVersion.md)
`price` | [Price](Price.md)
`status` | [LicenseStatus](LicenseStatus.md)
`updatedAt` | Date

## Example

```typescript
import type { License } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": l3Nv8KwB,
  "productId": x7Kp2QaZ,
  "policyId": p4Rt8LmQ,
  "customerId": c9Wd3RtE,
  "key": 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF,
  "createdAt": 2026-01-15T09:30:00.000Z,
  "expiresAt": 2027-01-15T09:30:00.000Z,
  "meta": {seats=5},
  "stripePaymentIntentId": pi_3MtwBwLkdIwHu7ix28a3tqPa,
  "maxMachines": 3,
  "maxOfflineDurationSeconds": 604800,
  "activeMachineCount": 2,
  "lastActivatedAt": 2026-03-02T14:05:00.000Z,
  "maxVersion": null,
  "price": null,
  "status": null,
  "updatedAt": 2026-01-15T09:30:00.000Z,
} satisfies License

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as License
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


