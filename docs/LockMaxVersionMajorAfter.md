
# LockMaxVersionMajorAfter

Time after the creation of a license its major version is locked, in seconds or calendar months: it then only gets the minor versions and bug fixes of the major version released by then. `0` locks it when the license is created.

## Properties

Name | Type
------------ | -------------
`value` | number
`unit` | string

## Example

```typescript
import type { LockMaxVersionMajorAfter } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "value": 12,
  "unit": null,
} satisfies LockMaxVersionMajorAfter

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LockMaxVersionMajorAfter
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


