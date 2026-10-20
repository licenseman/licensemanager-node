
# PortalNotFound


## Properties

Name | Type
------------ | -------------
`error` | [ErrorError](ErrorError.md)
`organizationSlug` | string
`productSlug` | string

## Example

```typescript
import type { PortalNotFound } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "error": null,
  "organizationSlug": acme,
  "productSlug": acme-pro,
} satisfies PortalNotFound

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as PortalNotFound
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


