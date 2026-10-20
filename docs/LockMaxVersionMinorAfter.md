
# LockMaxVersionMinorAfter

Time after the creation of a license its minor version is locked, in seconds or calendar months: it then only gets the bug fixes of the minor version released by then. Never shorter than `majorAfter`, whatever the length of the months: 1 month is longer than 28 days but may be shorter than 31. `0` locks it when the license is created. `null` to never lock it.

## Properties

Name | Type
------------ | -------------
`value` | number
`unit` | string

## Example

```typescript
import type { LockMaxVersionMinorAfter } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "value": 12,
  "unit": null,
} satisfies LockMaxVersionMinorAfter

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LockMaxVersionMinorAfter
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


