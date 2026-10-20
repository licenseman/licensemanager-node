
# LicenseMaxVersion

Latest version of the product the license can use: its hard-coded `version`, else the versions released before its locks. All `null` when it can use every version.

## Properties

Name | Type
------------ | -------------
`version` | string
`lockMajorAt` | Date
`lockMinorAt` | Date

## Example

```typescript
import type { LicenseMaxVersion } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "version": 2.3,
  "lockMajorAt": 2026-02-15T09:30:00.000Z,
  "lockMinorAt": 2027-01-15T09:30:00.000Z,
} satisfies LicenseMaxVersion

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LicenseMaxVersion
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


