
# PaddleIntegration


## Properties

Name | Type
------------ | -------------
`livemode` | boolean
`webhookUrlReachable` | boolean
`requiredPermissions` | [Array&lt;PaddlePermission&gt;](PaddlePermission.md)
`integration` | [Integration](Integration.md)
`mappings` | [Array&lt;IntegrationMapping&gt;](IntegrationMapping.md)

## Example

```typescript
import type { PaddleIntegration } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "livemode": null,
  "webhookUrlReachable": null,
  "requiredPermissions": null,
  "integration": null,
  "mappings": null,
} satisfies PaddleIntegration

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as PaddleIntegration
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


