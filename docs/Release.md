
# Release


## Properties

Name | Type
------------ | -------------
`id` | string
`productId` | string
`version` | string
`releasedAt` | Date
`createdAt` | Date
`activeMachineCount` | number

## Example

```typescript
import type { Release } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": r4Lm8VwX,
  "productId": x7Kp2QaZ,
  "version": 2.3.1,
  "releasedAt": 2026-03-01T12:00:00.000Z,
  "createdAt": 2026-03-01T12:00:00.000Z,
  "activeMachineCount": 12,
} satisfies Release

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Release
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


