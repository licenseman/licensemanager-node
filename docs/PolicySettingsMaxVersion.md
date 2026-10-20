
# PolicySettingsMaxVersion

Latest version of the product the licenses created with this policy can use. `null` allows every version. Defaults to `null`.  - `fixed`: up to a hard-coded `version`. `\"2\"` allows every 2.y.z version: its minor versions and bug fixes. `\"2.3\"` allows every 2.3.z version: its bug fixes. - `lock`: every version released during some time after the license is created, then only the updates of the version reached by then. The major version locks `majorAfter` the creation of the license, then the license only gets the minor versions and bug fixes of its major version. The minor version optionally locks `minorAfter` it, never sooner than the major version, then the license only gets the bug fixes of its minor version. `{ \"type\": \"lock\", \"majorAfter\": { \"value\": 1, \"unit\": \"months\" }, \"minorAfter\": { \"value\": 12, \"unit\": \"months\" } }` allows every version released during the month after the license is created, then the minor versions and bug fixes of the major version reached by then until the end of the first year, then only the bug fixes of the minor version reached by then. `majorAfter` at 0 allows minor versions only, and both at 0 allows bug fixes only: no updates.  Bug fixes are never locked: a hard-coded version has no patch number, like `\"2.3.1\"`, and a lock only locks major and minor versions.

## Properties

Name | Type
------------ | -------------
`type` | string
`version` | string
`majorAfter` | [LockMaxVersionMajorAfter](LockMaxVersionMajorAfter.md)
`minorAfter` | [LockMaxVersionMinorAfter](LockMaxVersionMinorAfter.md)

## Example

```typescript
import type { PolicySettingsMaxVersion } from '@licenseman/sdk'

// TODO: Update the object below with actual values
const example = {
  "type": null,
  "version": 2.3,
  "majorAfter": null,
  "minorAfter": null,
} satisfies PolicySettingsMaxVersion

console.log(example)

// Convert the instance to a JSON string
const exampleJSON: string = JSON.stringify(example)
console.log(exampleJSON)

// Parse the JSON string back to an object
const exampleParsed = JSON.parse(exampleJSON) as PolicySettingsMaxVersion
console.log(exampleParsed)
```

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


