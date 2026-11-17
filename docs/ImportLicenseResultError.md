
# ImportLicenseResultError

Why it wasn\'t imported. `key_taken` when skipped. `policy_not_found`, `validation_error`, `integration_not_connected`, `integration_error`, `subscription_not_found`, `subscription_not_mapped` or `subscription_taken` when failed.

## Properties

Name | Type
------------ | -------------
`code` | string
`message` | string

## Example

```typescript
import type { ImportLicenseResultError } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "code": null,
  "message": null,
} satisfies ImportLicenseResultError

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ImportLicenseResultError
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


