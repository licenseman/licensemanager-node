
# UpdateRelease


## Properties

Name | Type
------------ | -------------
`version` | string
`releasedAt` | Date

## Example

```typescript
import type { UpdateRelease } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "version": 2.3.1,
  "releasedAt": 2026-03-01T12:00:00.000Z,
} satisfies UpdateRelease

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as UpdateRelease
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


