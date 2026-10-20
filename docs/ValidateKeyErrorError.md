
# ValidateKeyErrorError


## Properties

Name | Type
------------ | -------------
`code` | string
`message` | string
`issues` | [Array&lt;ErrorErrorIssuesInner&gt;](ErrorErrorIssuesInner.md)
`latestAllowedVersion` | string

## Example

```typescript
import type { ValidateKeyErrorError } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "code": not_found,
  "message": Resource not found,
  "issues": null,
  "latestAllowedVersion": 2.3.1,
} satisfies ValidateKeyErrorError

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ValidateKeyErrorError
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


