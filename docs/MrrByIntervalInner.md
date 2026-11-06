
# MrrByIntervalInner


## Properties

Name | Type
------------ | -------------
`interval` | string
`intervalCount` | number
`subscriptionCount` | number
`mrr` | number

## Example

```typescript
import type { MrrByIntervalInner } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "interval": null,
  "intervalCount": 1,
  "subscriptionCount": 80,
  "mrr": 800,
} satisfies MrrByIntervalInner

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as MrrByIntervalInner
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


