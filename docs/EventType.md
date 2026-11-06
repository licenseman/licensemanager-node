
# EventType

- `policy.created`: `payload` holds the policy\'s settings. - `policy.updated`: `payload.changes` maps each changed field to its previous (`from`) and new (`to`) value. Making a policy the default also updates the previous default one. - `license.created`: `payload` holds the license\'s key, `policyId`, `customerId` and settings. Not linked to the policy. - `license.updated`: `payload.changes`, like `policy.updated`. - `license.validated`: a machine validated the license key. `payload` holds the machine\'s `fingerprint`, `name` and `version`, whether the validation created the machine (`machineCreated`) or activated it again (`machineActivated`), the `overriddenMachineId` of the machine it deactivated to take its place, `null` when none, and the `lockedMachineIds` of the machines it locked as it took its place back (see `validateKey`). - `license.validation_failed`: validating the license key failed. `payload` holds the error `code` and `message`, and the `fingerprint`, `name`, `platform` and `version` sent, the name and platform being the machine\'s when none is sent. Linked to the machine when it exists. - `license.canceled`: the license was canceled. `payload` holds the cancellation `reason` and `comment`, and whether its Stripe payment is being refunded (`refund`). - `license.refunded`: the Stripe payment of a canceled license was refunded. `payload` holds the Stripe `refundId` and the `amount` refunded. Has the `integration` actor. - `license.refund_failed`: refunding the Stripe payment of a canceled license failed. `payload` holds the error `message`: refund it from Stripe. Has the `integration` actor. - `license.payment_succeeded`: a payment of the license\'s Stripe subscription succeeded, its first one included. `payload` holds the Stripe `invoiceId`, the `amount` paid before taxes and its `currency`, Stripe\'s `billingReason` (`subscription_create`, `subscription_cycle`, `subscription_update`…) and the `periodStart` and `periodEnd` it pays for. Invoices with nothing to pay, like for a trial, record none. Has the `integration` actor. - `license.payment_failed`: a payment of the license\'s Stripe subscription failed. `payload` holds the Stripe `invoiceId`, the `amount` due and its `currency`, the `attemptCount` and when Stripe tries again (`nextAttemptAt`, `null` when it won\'t). The license stays valid for the integration\'s grace days after its period ends. Has the `integration` actor. - `license.subscription_ended`: the license\'s Stripe subscription ended, canceled or no longer paid, so the license expired. `payload` holds the subscription\'s `status` and Stripe\'s cancellation `reason`. Has the `integration` actor. - `machine.deactivated`: a machine was deactivated or locked, so it no longer counts as using the license. `payload` holds the machine\'s `fingerprint` and `name`, the `overriddenByMachineId` of the machine that took its place, `null` when it was deactivated through the API, and whether it was `locked`. Deactivations by validations have the `automation` actor. Linked to the license and the machine.  An update that changes nothing records no event. Deletions record no events, and customers, products and releases have none.

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


