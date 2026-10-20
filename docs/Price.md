
# Price

Price paid for a license. Licenses have `null` instead when it\'s unknown, which leaves them out of the revenue stats.

## Properties

Name | Type
------------ | -------------
`amount` | number
`currency` | string

## Example

```typescript
import type { Price } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "amount": 49.99,
  "currency": USD,
} satisfies Price

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as Price
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


