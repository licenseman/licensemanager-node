
# PaddlePrice


## Properties

Name | Type
------------ | -------------
`id` | string
`productId` | string
`productName` | string
`description` | string
`price` | [Price](Price.md)
`recurring` | [StripePriceRecurring](StripePriceRecurring.md)
`mapped` | boolean

## Example

```typescript
import type { PaddlePrice } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "id": pri_01gsz8x8sawmvhz1pv30nge1ke,
  "productId": pro_01gsz4t5hdjse780zja8vvr7jg,
  "productName": Acme Pro,
  "description": Launch price,
  "price": null,
  "recurring": null,
  "mapped": null,
} satisfies PaddlePrice

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as PaddlePrice
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


