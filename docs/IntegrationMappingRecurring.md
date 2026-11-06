
# IntegrationMappingRecurring

Billing period of a recurring price, `null` for a one-time price. Subscribing to a recurring price creates one subscription license, valid while it\'s paid.

## Properties

Name | Type
------------ | -------------
`interval` | string
`intervalCount` | number

## Example

```typescript
import type { IntegrationMappingRecurring } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "interval": null,
  "intervalCount": 1,
} satisfies IntegrationMappingRecurring

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as IntegrationMappingRecurring
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


