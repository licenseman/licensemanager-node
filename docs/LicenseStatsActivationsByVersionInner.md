
# LicenseStatsActivationsByVersionInner


## Properties

Name | Type
------------ | -------------
`version` | string
`counts` | Array&lt;number&gt;

## Example

```typescript
import type { LicenseStatsActivationsByVersionInner } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "version": null,
  "counts": [0, 3, 1],
} satisfies LicenseStatsActivationsByVersionInner

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LicenseStatsActivationsByVersionInner
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


