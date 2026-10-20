
# EventType

- `policy.created`: `payload` holds the policy\'s settings. - `policy.updated`: `payload.changes` maps each changed field to its previous (`from`) and new (`to`) value. Making a policy the default also updates the previous default one. - `license.created`: `payload` holds the license\'s key, `policyId`, `customerId` and settings. Not linked to the policy. - `license.updated`: `payload.changes`, like `policy.updated`. - `license.validated`: a machine validated the license key. `payload` holds the machine\'s `fingerprint`, `name` and `version`, and whether the validation created the machine (`machineCreated`) or activated it again (`machineActivated`). - `license.validation_failed`: validating the license key failed. `payload` holds the error `code` and `message`, and the `fingerprint`, `name`, `platform` and `version` sent, the name and platform being the machine\'s when none is sent. Linked to the machine when it exists. - `machine.deactivated`: a machine was deactivated, so it no longer counts as using the license. `payload` holds the machine\'s `fingerprint` and `name`. Linked to the license and the machine.  An update that changes nothing records no event. Deletions record no events, and customers, products and releases have none.

## Properties

Name | Type
------------ | -------------

## Example

```typescript
import type { EventType } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
} satisfies EventType

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as EventType
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


