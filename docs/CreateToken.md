
# CreateToken


## Properties

Name | Type
------------ | -------------
`scope` | Array&lt;string&gt;
`expiresInSeconds` | number

## Example

```typescript
import type { CreateToken } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "scope": [license:read, machine:write],
  "expiresInSeconds": 3600,
} satisfies CreateToken

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CreateToken
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


