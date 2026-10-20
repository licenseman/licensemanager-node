
# CreateIntegrationMapping


## Properties

Name | Type
------------ | -------------
`stripePriceId` | string
`policyId` | string

## Example

```typescript
import type { CreateIntegrationMapping } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "stripePriceId": price_1MoBy5LkdIwHu7ix,
  "policyId": p4Rt8LmQ,
} satisfies CreateIntegrationMapping

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateIntegrationMapping
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


