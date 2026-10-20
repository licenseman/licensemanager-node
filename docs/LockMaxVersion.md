
# LockMaxVersion

The licenses can use every version released after their creation, until their major version locks `majorAfter` it, then the updates of their major version until their minor version locks `minorAfter` it, if ever. Bug fixes are never locked.

## Properties

Name | Type
------------ | -------------
`type` | string
`majorAfter` | [LockMaxVersionMajorAfter](LockMaxVersionMajorAfter.md)
`minorAfter` | [LockMaxVersionMinorAfter](LockMaxVersionMinorAfter.md)

## Example

```typescript
import type { LockMaxVersion } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "type": null,
  "majorAfter": null,
  "minorAfter": null,
} satisfies LockMaxVersion

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as LockMaxVersion
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


