
# UpdateProduct


## Properties

Name | Type
------------ | -------------
`name` | string
`slug` | string
`portal` | [UpdateProductPortal](UpdateProductPortal.md)

## Example

```typescript
import type { UpdateProduct } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "name": Acme Pro,
  "slug": acme-pro,
  "portal": null,
} satisfies UpdateProduct

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as UpdateProduct
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


