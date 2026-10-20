
# EventActor

Who caused the event: a user of the app, an API key, a token, `automation` for the changes the app makes on its own, like applying the version locks, or `integration` for the changes of an integration, like the licenses a Stripe payment creates. `null` for requests that don\'t authenticate, like validating a license key.

## Properties

Name | Type
------------ | -------------
`type` | string
`id` | string
`name` | string
`email` | string
`image` | string
`start` | string
`tokenType` | string
`subjectId` | string
`provider` | string

## Example

```typescript
import type { EventActor } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "type": null,
  "id": i8Fz4QnRt,
  "name": Billing backend,
  "email": jane@example.com,
  "image": https://example.com/jane.png,
  "start": lm_Ab3d,
  "tokenType": null,
  "subjectId": m9Tq3VhD,
  "provider": null,
} satisfies EventActor

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as EventActor
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


