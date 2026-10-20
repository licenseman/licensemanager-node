
# IntegrationMapping


## Properties

Name | Type
------------ | -------------
`id` | string
`integrationId` | string
`productId` | string
`policyId` | string
`stripeProductId` | string
`stripePriceId` | string
`productName` | string
`price` | [Price](Price.md)
`status` | string
`statusReason` | string
`createdAt` | Date

## Example

```typescript
import type { IntegrationMapping } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": g2Lk7RwPa,
  "integrationId": i8Fz4QnRt,
  "productId": x7Kp2QaZ,
  "policyId": p4Rt8LmQ,
  "stripeProductId": prod_NWjs8kKbJWmuuc,
  "stripePriceId": price_1MoBy5LkdIwHu7ix,
  "productName": Acme Pro,
  "price": null,
  "status": null,
  "statusReason": The price is archived in Stripe,
  "createdAt": null,
} satisfies IntegrationMapping

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as IntegrationMapping
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


