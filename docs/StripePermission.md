
# StripePermission


## Properties

Name | Type
------------ | -------------
`resource` | string
`access` | string
`reason` | string

## Example

```typescript
import type { StripePermission } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "resource": Prices,
  "access": null,
  "reason": Lists your prices so you can choose which ones create licenses, and checks they can still be paid.,
} satisfies StripePermission

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as StripePermission
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


