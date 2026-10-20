
# CreateProduct


## Properties

Name | Type
------------ | -------------
`name` | string
`slug` | string

## Example

```typescript
import type { CreateProduct } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "name": Acme Pro,
  "slug": acme-pro,
} satisfies CreateProduct

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateProduct
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


