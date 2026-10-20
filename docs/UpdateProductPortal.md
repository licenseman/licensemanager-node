
# UpdateProductPortal


## Properties

Name | Type
------------ | -------------
`enabled` | boolean
`brandColor` | string
`accentColor` | string
`returnUrl` | string
`returnDomains` | Array&lt;string&gt;

## Example

```typescript
import type { UpdateProductPortal } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "enabled": true,
  "brandColor": #1e3a8a,
  "accentColor": #2563eb,
  "returnUrl": https://example.com/account,
  "returnDomains": [example.com],
} satisfies UpdateProductPortal

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as UpdateProductPortal
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


