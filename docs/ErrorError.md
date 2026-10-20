
# ErrorError


## Properties

Name | Type
------------ | -------------
`code` | string
`message` | string
`issues` | [Array&lt;ErrorErrorIssuesInner&gt;](ErrorErrorIssuesInner.md)

## Example

```typescript
import type { ErrorError } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "code": not_found,
  "message": Resource not found,
  "issues": null,
} satisfies ErrorError

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ErrorError
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


