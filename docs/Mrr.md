
# Mrr


## Properties

Name | Type
------------ | -------------
`currency` | string
`mrr` | number
`byInterval` | [Array&lt;MrrByIntervalInner&gt;](MrrByIntervalInner.md)
`byPolicy` | [Array&lt;MrrByPolicyInner&gt;](MrrByPolicyInner.md)
`byMonth` | Array&lt;number&gt;

## Example

```typescript
import type { Mrr } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "currency": USD,
  "mrr": 1240,
  "byInterval": null,
  "byPolicy": null,
  "byMonth": [900, 1100, 1240],
} satisfies Mrr

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Mrr
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


