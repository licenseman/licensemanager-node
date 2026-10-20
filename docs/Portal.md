
# Portal


## Properties

Name | Type
------------ | -------------
`productId` | string
`productName` | string
`organizationName` | string
`logoUrl` | string
`brandColor` | string
`accentColor` | string
`returnUrl` | string

## Example

```typescript
import type { Portal } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "productId": x7Kp2QaZ,
  "productName": Acme Pro,
  "organizationName": Acme,
  "logoUrl": https://cdn.example.com/logos/x7Kp2QaZ/k3f9a2LpQ7xw.webp,
  "brandColor": #1e3a8a,
  "accentColor": #2563eb,
  "returnUrl": https://example.com/account,
} satisfies Portal

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Portal
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


