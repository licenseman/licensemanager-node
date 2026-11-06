
# SlackConnection


## Properties

Name | Type
------------ | -------------
`id` | string
`teamId` | string
`teamName` | string
`channelId` | string
`channelName` | string
`configurationUrl` | string
`events` | Array&lt;string&gt;
`status` | string
`statusReason` | string
`lastSentAt` | Date
`createdAt` | Date

## Example

```typescript
import type { SlackConnection } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": s4Hq8ZpLm,
  "teamId": T0123ABCD,
  "teamName": Acme,
  "channelId": C0456EFGH,
  "channelName": #sales,
  "configurationUrl": null,
  "events": null,
  "status": null,
  "statusReason": null,
  "lastSentAt": null,
  "createdAt": null,
} satisfies SlackConnection

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as SlackConnection
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


