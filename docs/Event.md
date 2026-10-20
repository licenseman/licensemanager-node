
# Event


## Properties

Name | Type
------------ | -------------
`id` | string
`type` | [EventType](EventType.md)
`createdAt` | Date
`payload` | { [key: string]: any | null; }
`policyId` | string
`licenseId` | string
`machineId` | string
`machine` | [EventMachine](EventMachine.md)
`actor` | [EventActor](EventActor.md)

## Example

```typescript
import type { Event } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": e6Pw2JcXa,
  "type": null,
  "createdAt": 2026-01-15T09:30:00.000Z,
  "payload": {fingerprint=4c:32:75:8f:9a:1e, version=1.4.2},
  "policyId": null,
  "licenseId": l3Nv8KwB,
  "machineId": m9Tq3VhD,
  "machine": null,
  "actor": null,
} satisfies Event

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Event
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


