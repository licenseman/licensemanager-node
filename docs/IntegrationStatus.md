
# IntegrationStatus

`active`: the integration works. `error`: something needs fixing, explained by `statusReason`, like a permission missing from the API key or a mapped price archived. `disconnected`: the API key no longer works, connect a new one.

## Properties

Name | Type
------------ | -------------

## Example

```typescript
import type { IntegrationStatus } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
} satisfies IntegrationStatus

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as IntegrationStatus
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


