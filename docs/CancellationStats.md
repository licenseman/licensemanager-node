
# CancellationStats

Cancellations of the licenses with a money back guarantee. Licenses canceled without one are left out.

## Properties

Name | Type
------------ | -------------
`licenseCount` | number
`canceledLicenseCount` | number
`cancellableLicenseCount` | number
`rate` | number
`canceledByDay` | Array&lt;number&gt;
`canceledByMonth` | Array&lt;number&gt;
`byReason` | [Array&lt;CancellationStatsByReasonInner&gt;](CancellationStatsByReasonInner.md)

## Example

```typescript
import type { CancellationStats } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "licenseCount": 80,
  "canceledLicenseCount": 4,
  "cancellableLicenseCount": 12,
  "rate": 0.05,
  "canceledByDay": [0, 1, 0],
  "canceledByMonth": [1, 0, 2],
  "byReason": null,
} satisfies CancellationStats

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as CancellationStats
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


