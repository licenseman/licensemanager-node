
# Revenue

Revenue in one currency: the licenses sold once, each counting on the day it was created, and the payments of the subscription licenses, each counting on the day it was paid, with the license\'s policy. Licenses without a price are left out, and so are canceled ones, but in `canceledLicenseCount` and `canceledTotal`.

## Properties

Name | Type
------------ | -------------
`currency` | string
`licenseCount` | number
`total` | number
`subscriptionTotal` | number
`paymentCount` | number
`canceledLicenseCount` | number
`canceledTotal` | number
`thisMonth` | number
`lastMonth` | number
`last30Days` | number
`byDay` | Array&lt;number&gt;
`byMonth` | Array&lt;number&gt;
`byPolicy` | [Array&lt;ProductStatsNewLicensesByPolicyInner&gt;](ProductStatsNewLicensesByPolicyInner.md)

## Example

```typescript
import type { Revenue } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "currency": USD,
  "licenseCount": 42,
  "total": 2099.58,
  "subscriptionTotal": 480,
  "paymentCount": 48,
  "canceledLicenseCount": 2,
  "canceledTotal": 99.98,
  "thisMonth": 349.93,
  "lastMonth": 299.94,
  "last30Days": 399.92,
  "byDay": [0, 49.99, 99.98],
  "byMonth": [199.96, 249.95, 349.93],
  "byPolicy": null,
} satisfies Revenue

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Revenue
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


