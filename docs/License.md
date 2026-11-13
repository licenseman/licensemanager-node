
# License


## Properties

Name | Type
------------ | -------------
`id` | string
`productId` | string
`policyId` | string
`customerId` | string
`customer` | [LicenseCustomer](LicenseCustomer.md)
`key` | string
`createdAt` | Date
`expiresAt` | Date
`meta` | { [key: string]: any | null; }
`stripePaymentIntentId` | string
`paddleTransactionId` | string
`maxMachines` | number
`maxOfflineDurationSeconds` | number
`activeMachineCount` | number
`lastActivatedAt` | Date
`maxVersion` | [LicenseMaxVersion](LicenseMaxVersion.md)
`price` | [Price](Price.md)
`status` | [LicenseStatus](LicenseStatus.md)
`cancellableUntil` | Date
`canceledAt` | Date
`cancellationReason` | [CancellationReason](CancellationReason.md)
`subscription` | [LicenseSubscription](LicenseSubscription.md)
`cancellationComment` | string
`stripeRefundId` | string
`paddleAdjustmentId` | string
`paddleRefundStatus` | string
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
  "customer": null,
  "key": 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF,
  "createdAt": 2026-01-15T09:30:00.000Z,
  "expiresAt": 2027-01-15T09:30:00.000Z,
  "meta": {seats=5},
  "stripePaymentIntentId": pi_3MtwBwLkdIwHu7ix28a3tqPa,
  "paddleTransactionId": txn_01h04vsc0qhwtsbsxh3422wjs4,
  "maxMachines": 3,
  "maxOfflineDurationSeconds": 604800,
  "activeMachineCount": 2,
  "lastActivatedAt": 2026-03-02T14:05:00.000Z,
  "maxVersion": null,
  "price": null,
  "status": null,
  "cancellableUntil": 2026-02-14T09:30:00.000Z,
  "canceledAt": 2026-01-20T16:12:00.000Z,
  "cancellationReason": null,
  "subscription": null,
  "cancellationComment": I only needed it for one project.,
  "stripeRefundId": re_3MtwBwLkdIwHu7ix0Bs5rA2b,
  "paddleAdjustmentId": adj_01h04vsc0qhwtsbsxh3422wjs4,
  "paddleRefundStatus": approved,
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


