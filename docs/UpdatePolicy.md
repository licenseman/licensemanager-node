
# UpdatePolicy


## Properties

Name | Type
------------ | -------------
`name` | string
`slug` | string
`isDefault` | boolean
`duration` | [PolicySettingsDuration](PolicySettingsDuration.md)
`maxMachines` | number
`maxOfflineDurationSeconds` | number
`maxVersion` | [PolicySettingsMaxVersion](PolicySettingsMaxVersion.md)

## Example

```typescript
import type { UpdatePolicy } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "name": Yearly,
  "slug": yearly,
  "isDefault": false,
  "duration": null,
  "maxMachines": 3,
  "maxOfflineDurationSeconds": 604800,
  "maxVersion": null,
} satisfies UpdatePolicy

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as UpdatePolicy
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


