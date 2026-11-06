
# CancellationStatsByReasonInner


## Properties

Name | Type
------------ | -------------
`reason` | [CancellationReason](CancellationReason.md)
`count` | number

## Example

```typescript
import type { CancellationStatsByReasonInner } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "reason": null,
  "count": 2,
} satisfies CancellationStatsByReasonInner

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CancellationStatsByReasonInner
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


