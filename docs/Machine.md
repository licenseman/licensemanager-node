
# Machine


## Properties

Name | Type
------------ | -------------
`id` | string
`licenseId` | string
`fingerprint` | string
`platform` | string
`name` | string
`status` | string
`version` | string
`lastValidatedAt` | Date
`createdAt` | Date
`updatedAt` | Date

## Example

```typescript
import type { Machine } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": m9Tq3VhD,
  "licenseId": l3Nv8KwB,
  "fingerprint": 4c:32:75:8f:9a:1e,
  "platform": macOS,
  "name": Jane's MacBook,
  "status": active,
  "version": 1.4.2,
  "lastValidatedAt": 2026-01-15T09:30:00.000Z,
  "createdAt": 2026-01-15T09:30:00.000Z,
  "updatedAt": 2026-01-15T09:30:00.000Z,
} satisfies Machine

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Machine
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


