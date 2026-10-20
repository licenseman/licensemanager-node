
# EventMachine

The machine the event is about, with its current name. `null` when the event has no machine or it has been deleted.

## Properties

Name | Type
------------ | -------------
`id` | string
`name` | string
`fingerprint` | string

## Example

```typescript
import type { EventMachine } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": m9Tq3VhD,
  "name": Jane's MacBook,
  "fingerprint": 4c:32:75:8f:9a:1e,
} satisfies EventMachine

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as EventMachine
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


