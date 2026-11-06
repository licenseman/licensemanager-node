
# CancelLicense


## Properties

Name | Type
------------ | -------------
`reason` | [CancellationReason](CancellationReason.md)
`comment` | string
`refund` | boolean

## Example

```typescript
import type { CancelLicense } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "reason": null,
  "comment": I only needed it for one project.,
  "refund": true,
} satisfies CancelLicense

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CancelLicense
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


