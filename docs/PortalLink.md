
# PortalLink


## Properties

Name | Type
------------ | -------------
`url` | string
`token` | string
`expiresAt` | Date

## Example

```typescript
import type { PortalLink } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "url": https://app.example.com/portal/x7Kp2QaZ?token=eyJhbGciOi…,
  "token": eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9…,
  "expiresAt": 2026-01-22T09:30:00.000Z,
} satisfies PortalLink

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as PortalLink
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


