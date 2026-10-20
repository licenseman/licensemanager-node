
# ValidateKey


## Properties

Name | Type
------------ | -------------
`key` | string
`fingerprint` | string
`version` | string
`name` | string
`platform` | string

## Example

```typescript
import type { ValidateKey } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "key": 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF,
  "fingerprint": 4c:32:75:8f:9a:1e,
  "version": 1.4.2,
  "name": Jane's MacBook,
  "platform": macOS,
} satisfies ValidateKey

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ValidateKey
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


