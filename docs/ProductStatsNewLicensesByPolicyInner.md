
# ProductStatsNewLicensesByPolicyInner


## Properties

Name | Type
------------ | -------------
`policyId` | string
`byDay` | Array&lt;number&gt;
`byMonth` | Array&lt;number&gt;

## Example

```typescript
import type { ProductStatsNewLicensesByPolicyInner } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "policyId": p4Rt8LmQ,
  "byDay": [0, 2, 1],
  "byMonth": [4, 9, 12],
} satisfies ProductStatsNewLicensesByPolicyInner

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ProductStatsNewLicensesByPolicyInner
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


