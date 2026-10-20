
# ErrorErrorIssuesInner


## Properties

Name | Type
------------ | -------------
`path` | [Array&lt;ErrorErrorIssuesInnerPathInner&gt;](ErrorErrorIssuesInnerPathInner.md)
`message` | string

## Example

```typescript
import type { ErrorErrorIssuesInner } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "path": [name],
  "message": Too small: expected string to have >=1 characters,
} satisfies ErrorErrorIssuesInner

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ErrorErrorIssuesInner
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


