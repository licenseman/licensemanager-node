
# FixedMaxVersion

The licenses can use up to `version`, whenever they\'re created.

## Properties

Name | Type
------------ | -------------
`type` | string
`version` | string

## Example

```typescript
import type { FixedMaxVersion } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "type": null,
  "version": 2.3,
} satisfies FixedMaxVersion

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as FixedMaxVersion
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


