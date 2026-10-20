
# LicenseStatsActivationsByMachineInner


## Properties

Name | Type
------------ | -------------
`machineId` | string
`name` | string
`fingerprint` | string
`counts` | Array&lt;number&gt;

## Example

```typescript
import type { LicenseStatsActivationsByMachineInner } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "machineId": m5Tq9HsJ,
  "name": Jane's MacBook,
  "fingerprint": 4c:32:75:8f:9a:1e,
  "counts": [0, 3, 1],
} satisfies LicenseStatsActivationsByMachineInner

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LicenseStatsActivationsByMachineInner
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


