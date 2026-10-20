
# PolicyDuration

Duration of the licenses created with this policy. `null` when they never expire.

## Properties

Name | Type
------------ | -------------
`value` | number
`unit` | string

## Example

```typescript
import type { PolicyDuration } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "value": 12,
  "unit": null,
} satisfies PolicyDuration

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as PolicyDuration
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


