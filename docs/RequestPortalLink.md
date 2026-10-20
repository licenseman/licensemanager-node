
# RequestPortalLink


## Properties

Name | Type
------------ | -------------
`email` | string
`returnUrl` | string

## Example

```typescript
import type { RequestPortalLink } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "email": jane@example.com,
  "returnUrl": https://example.com/account,
} satisfies RequestPortalLink

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as RequestPortalLink
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


