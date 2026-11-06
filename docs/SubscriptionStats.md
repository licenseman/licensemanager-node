
# SubscriptionStats

Subscriptions to recurring Stripe prices, each with its subscription license.

## Properties

Name | Type
------------ | -------------
`activeCount` | number
`trialingCount` | number
`pastDueCount` | number
`cancelingCount` | number
`newCount` | number
`endedCount` | number
`churnRate` | number
`newByMonth` | Array&lt;number&gt;
`endedByMonth` | Array&lt;number&gt;
`activeByMonth` | Array&lt;number&gt;
`mrr` | [Array&lt;Mrr&gt;](Mrr.md)

## Example

```typescript
import type { SubscriptionStats } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "activeCount": 120,
  "trialingCount": 4,
  "pastDueCount": 3,
  "cancelingCount": 5,
  "newCount": 14,
  "endedCount": 3,
  "churnRate": 0.025,
  "newByMonth": [3, 5, 8],
  "endedByMonth": [0, 1, 2],
  "activeByMonth": [90, 104, 120],
  "mrr": null,
} satisfies SubscriptionStats

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as SubscriptionStats
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


