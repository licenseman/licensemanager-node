
# Policy


## Properties

Name | Type
------------ | -------------
`id` | string
`productId` | string
`slug` | string
`name` | string
`isDefault` | boolean
`duration` | [PolicyDuration](PolicyDuration.md)
`maxMachines` | number
`maxOfflineDurationSeconds` | number
`maxVersion` | [PolicyMaxVersion](PolicyMaxVersion.md)
`licenseCount` | number
`createdAt` | Date
`updatedAt` | Date

## Example

```typescript
import type { Policy } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": p4Rt8LmQ,
  "productId": x7Kp2QaZ,
  "slug": yearly,
  "name": Yearly,
  "isDefault": false,
  "duration": null,
  "maxMachines": 3,
  "maxOfflineDurationSeconds": 604800,
  "maxVersion": null,
  "licenseCount": 12,
  "createdAt": 2026-01-15T09:30:00.000Z,
  "updatedAt": 2026-01-15T09:30:00.000Z,
} satisfies Policy

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Policy
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


