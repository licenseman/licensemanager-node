
# ImportLicenseSubscription

Subscription of the provider keeping the license valid, like one moved to Stripe by Lemon Squeezy\'s migration: its renewals then extend this license rather than creating one with a new key. Its price must be mapped to a policy of the product, which the license follows instead of `policyId`, and the license\'s expiration, version and money back guarantee follow the subscription like the ones it creates. Read from the provider of the product\'s mode, through the integration.

## Properties

Name | Type
------------ | -------------
`provider` | string
`externalId` | string

## Example

```typescript
import type { ImportLicenseSubscription } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "provider": null,
  "externalId": sub_1MowQVLkdIwHu7ix,
} satisfies ImportLicenseSubscription

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ImportLicenseSubscription
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


