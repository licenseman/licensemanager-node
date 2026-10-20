
# LicenseToken


## Properties

Name | Type
------------ | -------------
`license` | string

## Example

```typescript
import type { LicenseToken } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "license": eyJhbGciOiJFZERTQSIsInR5cCI6IkpXVCIsImtpZCI6Ims4UjJ2TnFXIn0…,
} satisfies LicenseToken

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LicenseToken
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


