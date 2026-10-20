
# EventActorOneOf


## Properties

Name | Type
------------ | -------------
`type` | string
`id` | string
`name` | string
`email` | string
`image` | string

## Example

```typescript
import type { EventActorOneOf } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "type": null,
  "id": u2Hk9PzLq,
  "name": Jane Doe,
  "email": jane@example.com,
  "image": https://example.com/jane.png,
} satisfies EventActorOneOf

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as EventActorOneOf
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


