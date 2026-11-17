
# ImportLicensesResult


## Properties

Name | Type
------------ | -------------
`created` | number
`skipped` | number
`failed` | number
`results` | [Array&lt;ImportLicenseResult&gt;](ImportLicenseResult.md)

## Example

```typescript
import type { ImportLicensesResult } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "created": null,
  "skipped": null,
  "failed": null,
  "results": null,
} satisfies ImportLicensesResult

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as ImportLicensesResult
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


