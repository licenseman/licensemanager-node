
# LicenseStats


## Properties

Name | Type
------------ | -------------
`from` | Date
`to` | Date
`days` | Array&lt;Date&gt;
`activationsByMachine` | [Array&lt;LicenseStatsActivationsByMachineInner&gt;](LicenseStatsActivationsByMachineInner.md)
`activationsByVersion` | [Array&lt;LicenseStatsActivationsByVersionInner&gt;](LicenseStatsActivationsByVersionInner.md)

## Example

```typescript
import type { LicenseStats } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "from": 2026-10-12,
  "to": 2026-10-12,
  "days": null,
  "activationsByMachine": null,
  "activationsByVersion": null,
} satisfies LicenseStats

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LicenseStats
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


