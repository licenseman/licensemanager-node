
# CreateProductWithPolicy


## Properties

Name | Type
------------ | -------------
`name` | string
`slug` | string
`defaultPolicy` | [PolicySettings](PolicySettings.md)
`isTestFromProductId` | string

## Example

```typescript
import type { CreateProductWithPolicy } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "name": Acme Pro,
  "slug": acme-pro,
  "defaultPolicy": null,
  "isTestFromProductId": x7Kp2QaZ,
} satisfies CreateProductWithPolicy

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateProductWithPolicy
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


