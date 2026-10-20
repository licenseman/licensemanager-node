
# Token


## Properties

Name | Type
------------ | -------------
`token` | string
`type` | string
`scope` | Array&lt;string&gt;
`expiresAt` | Date

## Example

```typescript
import type { Token } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "token": eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9…,
  "type": license,
  "scope": [license:read, machine:write],
  "expiresAt": 2026-01-15T10:30:00.000Z,
} satisfies Token

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Token
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


