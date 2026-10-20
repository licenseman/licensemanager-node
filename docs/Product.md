
# Product


## Properties

Name | Type
------------ | -------------
`id` | string
`slug` | string
`name` | string
`isTestFromProductId` | string
`logoUrl` | string
`portal` | [PortalSettings](PortalSettings.md)
`createdAt` | Date
`updatedAt` | Date

## Example

```typescript
import type { Product } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": x7Kp2QaZ,
  "slug": acme-pro,
  "name": Acme Pro,
  "isTestFromProductId": null,
  "logoUrl": https://cdn.example.com/logos/x7Kp2QaZ/k3f9a2LpQ7xw.webp,
  "portal": null,
  "createdAt": 2026-01-15T09:30:00.000Z,
  "updatedAt": 2026-01-15T09:30:00.000Z,
} satisfies Product

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Product
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


