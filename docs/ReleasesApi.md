# ReleasesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createRelease**](ReleasesApi.md#createrelease) | **POST** /v1/products/{productId}/releases | Create a release |
| [**deleteRelease**](ReleasesApi.md#deleterelease) | **DELETE** /v1/releases/{id} | Delete a release |
| [**getRelease**](ReleasesApi.md#getrelease) | **GET** /v1/releases/{id} | Get a release |
| [**listReleases**](ReleasesApi.md#listreleases) | **GET** /v1/products/{productId}/releases | List the releases of a product |
| [**updateRelease**](ReleasesApi.md#updaterelease) | **PATCH** /v1/releases/{id} | Update a release |



## createRelease

> Release createRelease(productId, createRelease)

Create a release

Releases don\&#39;t restrict which versions &#x60;validateKey&#x60; accepts: a machine can run a version without a release. They give the &#x60;latestAllowedVersion&#x60; of its &#x60;version_not_allowed&#x60; errors, among the stable releases already released, and the number of active machines running each version.  **Required role permission**: &#x60;release:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ReleasesApi,
} from '@licenseman/sdk';
import type { CreateReleaseRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ReleasesApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // CreateRelease
    createRelease: ...,
  } satisfies CreateReleaseRequest;

  try {
    const data = await api.createRelease(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **productId** | `string` |  | [Defaults to `undefined`] |
| **createRelease** | [CreateRelease](CreateRelease.md) |  | |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created release |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **409** | &#x60;version_taken&#x60;: version already released for the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteRelease

> deleteRelease(id)

Delete a release

**Required role permission**: &#x60;release:delete&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ReleasesApi,
} from '@licenseman/sdk';
import type { DeleteReleaseRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ReleasesApi(config);

  const body = {
    // string
    id: r4Lm8VwX,
  } satisfies DeleteReleaseRequest;

  try {
    const data = await api.deleteRelease(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **id** | `string` |  | [Defaults to `undefined`] |

### Return type

`void` (Empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Deleted |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Release not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getRelease

> Release getRelease(id)

Get a release

### Example

```ts
import {
  Configuration,
  ReleasesApi,
} from '@licenseman/sdk';
import type { GetReleaseRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ReleasesApi(config);

  const body = {
    // string
    id: r4Lm8VwX,
  } satisfies GetReleaseRequest;

  try {
    const data = await api.getRelease(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **id** | `string` |  | [Defaults to `undefined`] |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Release |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Release not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listReleases

> ReleaseList listReleases(productId, page, pageSize, sort, search, releasedFrom, releasedTo, activeMachineCount, activeMachineCountMin, activeMachineCountMax)

List the releases of a product

Sorting by &#x60;version&#x60; compares the major, minor and patch numbers as numbers, then puts a pre-release before its stable release. Pre-releases of the same version compare as text, unlike semantic versioning: &#x60;2.0.0-beta.10&#x60; comes before &#x60;2.0.0-beta.2&#x60;. Build metadata is ignored.

### Example

```ts
import {
  Configuration,
  ReleasesApi,
} from '@licenseman/sdk';
import type { ListReleasesRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ReleasesApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // number | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional)
    page: 1,
    // number | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional)
    pageSize: 20,
    // 'version' | '-version' | 'releasedAt' | '-releasedAt' | 'createdAt' | '-createdAt' | 'activeMachineCount' | '-activeMachineCount' | Field to sort by, prefixed with `-` for descending order. Defaults to `-version`. (optional)
    sort: -version,
    // string | Case-insensitive text the version contains. (optional)
    search: 2.3,
    // Date | Only returns the releases released at or after this date. (optional)
    releasedFrom: 2026-01-01T00:00:00.000Z,
    // Date | Only returns the releases released at or before this date. (optional)
    releasedTo: 2026-02-01T00:00:00.000Z,
    // number | Only returns the releases running on exactly this number of active machines. (optional)
    activeMachineCount: 1,
    // number | Only returns the releases running on at least this number of active machines. (optional)
    activeMachineCountMin: 1,
    // number | Only returns the releases running on at most this number of active machines. (optional)
    activeMachineCountMax: 1,
  } satisfies ListReleasesRequest;

  try {
    const data = await api.listReleases(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **productId** | `string` |  | [Defaults to `undefined`] |
| **page** | `number` | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [Optional] [Defaults to `1`] |
| **pageSize** | `number` | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [Optional] [Defaults to `20`] |
| **sort** | `version`, `-version`, `releasedAt`, `-releasedAt`, `createdAt`, `-createdAt`, `activeMachineCount`, `-activeMachineCount` | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-version&#x60;. | [Optional] [Defaults to `&#39;-version&#39;`] [Enum: version, -version, releasedAt, -releasedAt, createdAt, -createdAt, activeMachineCount, -activeMachineCount] |
| **search** | `string` | Case-insensitive text the version contains. | [Optional] [Defaults to `undefined`] |
| **releasedFrom** | `Date` | Only returns the releases released at or after this date. | [Optional] [Defaults to `undefined`] |
| **releasedTo** | `Date` | Only returns the releases released at or before this date. | [Optional] [Defaults to `undefined`] |
| **activeMachineCount** | `number` | Only returns the releases running on exactly this number of active machines. | [Optional] [Defaults to `undefined`] |
| **activeMachineCountMin** | `number` | Only returns the releases running on at least this number of active machines. | [Optional] [Defaults to `undefined`] |
| **activeMachineCountMax** | `number` | Only returns the releases running on at most this number of active machines. | [Optional] [Defaults to `undefined`] |

### Return type

[**ReleaseList**](ReleaseList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the releases of the product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## updateRelease

> Release updateRelease(id, updateRelease)

Update a release

**Required role permission**: &#x60;release:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ReleasesApi,
} from '@licenseman/sdk';
import type { UpdateReleaseRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ReleasesApi(config);

  const body = {
    // string
    id: r4Lm8VwX,
    // UpdateRelease
    updateRelease: ...,
  } satisfies UpdateReleaseRequest;

  try {
    const data = await api.updateRelease(body);
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters


| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **id** | `string` |  | [Defaults to `undefined`] |
| **updateRelease** | [UpdateRelease](UpdateRelease.md) |  | |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated release |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Release not found |  -  |
| **409** | &#x60;version_taken&#x60;: version already released for the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

