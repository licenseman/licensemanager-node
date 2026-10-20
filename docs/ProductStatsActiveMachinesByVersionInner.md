
# ProductStatsActiveMachinesByVersionInner


## Properties

Name | Type
------------ | -------------
`version` | string
`count` | number

## Example

```typescript
import type { ProductStatsActiveMachinesByVersionInner } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "version": 1.10.0,
  "count": 42,
} satisfies ProductStatsActiveMachinesByVersionInner

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ProductStatsActiveMachinesByVersionInner
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


