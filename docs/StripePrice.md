
# StripePrice


## Properties

Name | Type
------------ | -------------
`id` | string
`productId` | string
`productName` | string
`nickname` | string
`price` | [Price](Price.md)
`mapped` | boolean

## Example

```typescript
import type { StripePrice } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": price_1MoBy5LkdIwHu7ix,
  "productId": prod_NWjs8kKbJWmuuc,
  "productName": Acme Pro,
  "nickname": Launch price,
  "price": null,
  "mapped": null,
} satisfies StripePrice

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as StripePrice
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


