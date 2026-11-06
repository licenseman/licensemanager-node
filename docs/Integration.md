
# Integration


## Properties

Name | Type
------------ | -------------
`id` | string
`provider` | string
`livemode` | boolean
`accountName` | string
`apiKeyHint` | string
`webhookUrl` | string
`status` | [IntegrationStatus](IntegrationStatus.md)
`statusReason` | string
`lastCheckedAt` | Date
`lastEventAt` | Date
`autoRefund` | boolean
`canRefund` | boolean
`canManageSubscriptions` | boolean
`canBillingPortal` | boolean
`subscriptionGraceDays` | number
`createdAt` | Date

## Example

```typescript
import type { Integration } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": i8Fz4QnRt,
  "provider": null,
  "livemode": null,
  "accountName": Acme Inc.,
  "apiKeyHint": rk_live_…Ab3d,
  "webhookUrl": https://api.licensemanager.dev/v1/webhooks/stripe/i8Fz4QnRt,
  "status": null,
  "statusReason": The API key can't manage webhook endpoints: give it the Webhook Endpoints: Write permission,
  "lastCheckedAt": null,
  "lastEventAt": null,
  "autoRefund": true,
  "canRefund": true,
  "canManageSubscriptions": true,
  "canBillingPortal": true,
  "subscriptionGraceDays": 7,
  "createdAt": null,
} satisfies Integration

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Integration
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


