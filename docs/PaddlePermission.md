
# PaddlePermission


## Properties

Name | Type
------------ | -------------
`resource` | string
`access` | string
`scope` | string
`reason` | string
`optional` | boolean
`subscriptions` | boolean

## Example

```typescript
import type { PaddlePermission } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "resource": Prices,
  "access": null,
  "scope": price.read,
  "reason": Lists your prices so you can choose which ones create licenses, and checks they can still be paid.,
  "optional": false,
  "subscriptions": false,
} satisfies PaddlePermission

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as PaddlePermission
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


