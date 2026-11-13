
# LicenseSubscription

The Stripe or Paddle subscription keeping the license valid, `null` when it isn\'t a subscription license. The license expires when it stops being paid, includes every update, and can\'t be canceled during a money back guarantee.

## Properties

Name | Type
------------ | -------------
`provider` | string
`externalId` | string
`stripeSubscriptionId` | string
`status` | string
`interval` | string
`intervalCount` | number
`quantity` | number
`price` | [Price](Price.md)
`currentPeriodEnd` | Date
`cancelAtPeriodEnd` | boolean
`endedAt` | Date

## Example

```typescript
import type { LicenseSubscription } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "provider": null,
  "externalId": sub_1MowQVLkdIwHu7ix,
  "stripeSubscriptionId": sub_1MowQVLkdIwHu7ix,
  "status": active,
  "interval": null,
  "intervalCount": 1,
  "quantity": 1,
  "price": null,
  "currentPeriodEnd": null,
  "cancelAtPeriodEnd": null,
  "endedAt": null,
} satisfies LicenseSubscription

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LicenseSubscription
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


