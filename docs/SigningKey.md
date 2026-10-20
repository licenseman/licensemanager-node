
# SigningKey


## Properties

Name | Type
------------ | -------------
`id` | string
`algorithm` | string
`publicKey` | string
`createdAt` | Date

## Example

```typescript
import type { SigningKey } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": k8R2vNqW,
  "algorithm": null,
  "publicKey": -----BEGIN PUBLIC KEY-----
MCowBQYDK2VwAyEA…
-----END PUBLIC KEY-----
,
  "createdAt": 2026-01-15T09:30:00.000Z,
} satisfies SigningKey

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as SigningKey
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


