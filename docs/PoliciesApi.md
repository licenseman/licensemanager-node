# PoliciesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createPolicy**](PoliciesApi.md#createpolicy) | **POST** /v1/products/{productId}/policies | Create a policy |
| [**deletePolicy**](PoliciesApi.md#deletepolicy) | **DELETE** /v1/policies/{id} | Delete a policy |
| [**getPolicy**](PoliciesApi.md#getpolicy) | **GET** /v1/policies/{id} | Get a policy |
| [**listPolicies**](PoliciesApi.md#listpolicies) | **GET** /v1/products/{productId}/policies | List the policies of a product |
| [**updatePolicy**](PoliciesApi.md#updatepolicy) | **PATCH** /v1/policies/{id} | Update a policy |



## createPolicy

> Policy createPolicy(productId, createPolicy)

Create a policy

Without a &#x60;slug&#x60;, the policy gets one derived from its name, made unique within the product by appending a dash and 3 random lowercase letters or digits when needed. An explicit &#x60;slug&#x60; is used as is: the request fails with a &#x60;409&#x60; when it\&#39;s taken.  With &#x60;isDefault: true&#x60;, the new policy replaces the product\&#39;s current default policy.  A product always has a default policy, so when it has no policies the new one becomes the default: the request fails with a &#x60;409&#x60; when &#x60;isDefault&#x60; is &#x60;false&#x60;.  **Required role permission**: &#x60;policy:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  PoliciesApi,
} from '@licenseman/sdk';
import type { CreatePolicyRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new PoliciesApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // CreatePolicy
    createPolicy: ...,
  } satisfies CreatePolicyRequest;

  try {
    const data = await api.createPolicy(body);
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
| **createPolicy** | [CreatePolicy](CreatePolicy.md) |  | |

### Return type

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created policy |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **409** | &#x60;slug_taken&#x60;: the explicit slug is already used by another policy of the product, or a concurrent request took the same slug first. &#x60;default_required&#x60;: &#x60;isDefault: false&#x60; for the first policy of the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deletePolicy

> deletePolicy(id)

Delete a policy

Deleting the default policy makes the oldest remaining policy of the product the default. The last policy of a product can\&#39;t be deleted, nor a policy that licenses follow. Its events can no longer be listed.  **Required role permission**: &#x60;policy:delete&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  PoliciesApi,
} from '@licenseman/sdk';
import type { DeletePolicyRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new PoliciesApi(config);

  const body = {
    // string
    id: p4Rt8LmQ,
  } satisfies DeletePolicyRequest;

  try {
    const data = await api.deletePolicy(body);
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
| **404** | Policy not found |  -  |
| **409** | &#x60;last_policy&#x60;: the policy is the last one of its product. &#x60;policy_in_use&#x60;: licenses follow it |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getPolicy

> Policy getPolicy(id)

Get a policy

### Example

```ts
import {
  Configuration,
  PoliciesApi,
} from '@licenseman/sdk';
import type { GetPolicyRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new PoliciesApi(config);

  const body = {
    // string
    id: p4Rt8LmQ,
  } satisfies GetPolicyRequest;

  try {
    const data = await api.getPolicy(body);
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

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Policy |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Policy not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listPolicies

> PolicyList listPolicies(productId, page, pageSize, sort, search, slug, isDefault, licenseCount, licenseCountMin, licenseCountMax)

List the policies of a product

&#x60;?isDefault&#x3D;true&#x60; returns the product\&#39;s default policy alone: a product always has exactly one. Sorting by &#x60;duration&#x60; counts months for their average length, about 30.4 days.

### Example

```ts
import {
  Configuration,
  PoliciesApi,
} from '@licenseman/sdk';
import type { ListPoliciesRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new PoliciesApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // number | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional)
    page: 1,
    // number | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional)
    pageSize: 20,
    // 'name' | '-name' | 'slug' | '-slug' | 'duration' | '-duration' | 'maxMachines' | '-maxMachines' | 'maxOfflineDurationSeconds' | '-maxOfflineDurationSeconds' | 'licenseCount' | '-licenseCount' | 'createdAt' | '-createdAt' | 'updatedAt' | '-updatedAt' | Field to sort by, prefixed with `-` for descending order. Defaults to `name`. (optional)
    sort: name,
    // string | Case-insensitive text the name or slug contains. (optional)
    search: pro,
    // string | Only returns the policy with this exact slug. (optional)
    slug: yearly,
    // 'true' | 'false' | `true` only returns the product\'s default policy, `false` only the other ones. (optional)
    isDefault: true,
    // number | Only returns the policies followed by exactly this number of licenses. (optional)
    licenseCount: 1,
    // number | Only returns the policies followed by at least this number of licenses. (optional)
    licenseCountMin: 1,
    // number | Only returns the policies followed by at most this number of licenses. (optional)
    licenseCountMax: 1,
  } satisfies ListPoliciesRequest;

  try {
    const data = await api.listPolicies(body);
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
| **sort** | `name`, `-name`, `slug`, `-slug`, `duration`, `-duration`, `maxMachines`, `-maxMachines`, `maxOfflineDurationSeconds`, `-maxOfflineDurationSeconds`, `licenseCount`, `-licenseCount`, `createdAt`, `-createdAt`, `updatedAt`, `-updatedAt` | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;name&#x60;. | [Optional] [Defaults to `&#39;name&#39;`] [Enum: name, -name, slug, -slug, duration, -duration, maxMachines, -maxMachines, maxOfflineDurationSeconds, -maxOfflineDurationSeconds, licenseCount, -licenseCount, createdAt, -createdAt, updatedAt, -updatedAt] |
| **search** | `string` | Case-insensitive text the name or slug contains. | [Optional] [Defaults to `undefined`] |
| **slug** | `string` | Only returns the policy with this exact slug. | [Optional] [Defaults to `undefined`] |
| **isDefault** | `true`, `false` | &#x60;true&#x60; only returns the product\&#39;s default policy, &#x60;false&#x60; only the other ones. | [Optional] [Defaults to `undefined`] [Enum: true, false] |
| **licenseCount** | `number` | Only returns the policies followed by exactly this number of licenses. | [Optional] [Defaults to `undefined`] |
| **licenseCountMin** | `number` | Only returns the policies followed by at least this number of licenses. | [Optional] [Defaults to `undefined`] |
| **licenseCountMax** | `number` | Only returns the policies followed by at most this number of licenses. | [Optional] [Defaults to `undefined`] |

### Return type

[**PolicyList**](PolicyList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the policies of the product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## updatePolicy

> Policy updatePolicy(id, updatePolicy)

Update a policy

&#x60;isDefault: true&#x60; makes the policy the product\&#39;s default, in place of the current one. A product always has a default policy, so the default can\&#39;t be unset with &#x60;isDefault: false&#x60;: make another policy the default instead.  Licenses copy the settings of their policy when they\&#39;re created, so changing them only affects the licenses created afterwards: update the existing licenses to change theirs.  **Required role permission**: &#x60;policy:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  PoliciesApi,
} from '@licenseman/sdk';
import type { UpdatePolicyRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new PoliciesApi(config);

  const body = {
    // string
    id: p4Rt8LmQ,
    // UpdatePolicy
    updatePolicy: ...,
  } satisfies UpdatePolicyRequest;

  try {
    const data = await api.updatePolicy(body);
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
| **updatePolicy** | [UpdatePolicy](UpdatePolicy.md) |  | |

### Return type

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated policy |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Policy not found |  -  |
| **409** | &#x60;slug_taken&#x60;: slug already used by another policy of the product. &#x60;default_required&#x60;: &#x60;isDefault: false&#x60; on the default policy |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

