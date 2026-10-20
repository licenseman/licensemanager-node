
# ProductStats


## Properties

Name | Type
------------ | -------------
`licenseCount` | number
`activeLicenseCount` | number
`newLicenseCount` | number
`expiringLicenseCount` | number
`expiredLicenseCount` | number
`activeMachineCount` | number
`inUseLicenseCount` | number
`seatCount` | number
`usedSeatCount` | number
`fullLicenseCount` | number
`days` | Array&lt;Date&gt;
`months` | Array&lt;string&gt;
`newLicensesByDay` | Array&lt;number&gt;
`newLicensesByMonth` | Array&lt;number&gt;
`newLicensesByPolicy` | [Array&lt;ProductStatsNewLicensesByPolicyInner&gt;](ProductStatsNewLicensesByPolicyInner.md)
`revenue` | [Array&lt;Revenue&gt;](Revenue.md)
`activationsByVersion` | [Array&lt;ProductStatsActivationsByVersionInner&gt;](ProductStatsActivationsByVersionInner.md)
`activeMachinesByVersion` | [Array&lt;ProductStatsActiveMachinesByVersionInner&gt;](ProductStatsActiveMachinesByVersionInner.md)
`activeMachinesByPlatform` | [Array&lt;ProductStatsActiveMachinesByPlatformInner&gt;](ProductStatsActiveMachinesByPlatformInner.md)

## Example

```typescript
import type { ProductStats } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "licenseCount": 120,
  "activeLicenseCount": 87,
  "newLicenseCount": 14,
  "expiringLicenseCount": 3,
  "expiredLicenseCount": 2,
  "activeMachineCount": 154,
  "inUseLicenseCount": 80,
  "seatCount": 200,
  "usedSeatCount": 130,
  "fullLicenseCount": 12,
  "days": null,
  "months": null,
  "newLicensesByDay": [0, 2, 1],
  "newLicensesByMonth": [4, 9, 12],
  "newLicensesByPolicy": null,
  "revenue": null,
  "activationsByVersion": null,
  "activeMachinesByVersion": null,
  "activeMachinesByPlatform": null,
} satisfies ProductStats

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ProductStats
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


