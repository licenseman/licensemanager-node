# MachinesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**deactivateMachine**](MachinesApi.md#deactivatemachine) | **POST** /v1/machines/{id}/deactivate | Deactivate a machine |
| [**getMachine**](MachinesApi.md#getmachine) | **GET** /v1/machines/{id} | Get a machine |
| [**listMachines**](MachinesApi.md#listmachines) | **GET** /v1/licenses/{licenseId}/machines | List the machines of a license |



## deactivateMachine

> Machine deactivateMachine(id)

Deactivate a machine

The machine no longer counts as using the license, freeing its place when the license has a maximum number of machines. Validating the license key on the machine activates it again, unless the license is on its maximum number of machines by then. Deactivating a deactivated machine does nothing.  The license token &#x60;validateKey&#x60; returned to the machine isn\&#39;t revoked: the application can keep running offline until it expires. Machines can\&#39;t be deleted: they\&#39;re deleted with their license.  **Token access**: customer, license, machine tokens with the &#x60;machine:write&#x60; permission (or the matching write one). A token reaches the machine it\&#39;s scoped to, or the machines of its license or customer.  **Required role permission**: &#x60;machine:deactivate&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  MachinesApi,
} from '@licenseman/sdk';
import type { DeactivateMachineRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
    // Configure HTTP bearer authorization: token
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new MachinesApi(config);

  const body = {
    // string
    id: m9Tq3VhD,
  } satisfies DeactivateMachineRequest;

  try {
    const data = await api.deactivateMachine(body);
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

[**Machine**](Machine.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Deactivated machine |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Machine not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getMachine

> Machine getMachine(id)

Get a machine

**Token access**: customer, license, machine tokens with the &#x60;machine:read&#x60; permission (or the matching write one). A token reaches the machine it\&#39;s scoped to, or the machines of its license or customer.

### Example

```ts
import {
  Configuration,
  MachinesApi,
} from '@licenseman/sdk';
import type { GetMachineRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
    // Configure HTTP bearer authorization: token
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new MachinesApi(config);

  const body = {
    // string
    id: m9Tq3VhD,
  } satisfies GetMachineRequest;

  try {
    const data = await api.getMachine(body);
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

[**Machine**](Machine.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Machine |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Machine not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listMachines

> MachineList listMachines(licenseId, page, pageSize, sort, search, fingerprint, status)

List the machines of a license

**Token access**: customer, license tokens with the &#x60;machine:read&#x60; permission (or the matching write one). A token reaches the license it\&#39;s scoped to, or the licenses of its customer.

### Example

```ts
import {
  Configuration,
  MachinesApi,
} from '@licenseman/sdk';
import type { ListMachinesRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
    // Configure HTTP bearer authorization: token
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new MachinesApi(config);

  const body = {
    // string
    licenseId: l3Nv8KwB,
    // number | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional)
    page: 1,
    // number | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional)
    pageSize: 20,
    // 'name' | '-name' | 'platform' | '-platform' | 'createdAt' | '-createdAt' | 'updatedAt' | '-updatedAt' | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional)
    sort: -createdAt,
    // string | Case-insensitive text the fingerprint or name contains. (optional)
    search: macbook,
    // string | Only returns the machine with this exact fingerprint. (optional)
    fingerprint: 4c:32:75:8f:9a:1e,
    // 'active' | 'deactivated' | Only returns the machines with this status. (optional)
    status: active,
  } satisfies ListMachinesRequest;

  try {
    const data = await api.listMachines(body);
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
| **licenseId** | `string` |  | [Defaults to `undefined`] |
| **page** | `number` | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [Optional] [Defaults to `1`] |
| **pageSize** | `number` | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [Optional] [Defaults to `20`] |
| **sort** | `name`, `-name`, `platform`, `-platform`, `createdAt`, `-createdAt`, `updatedAt`, `-updatedAt` | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [Optional] [Defaults to `&#39;-createdAt&#39;`] [Enum: name, -name, platform, -platform, createdAt, -createdAt, updatedAt, -updatedAt] |
| **search** | `string` | Case-insensitive text the fingerprint or name contains. | [Optional] [Defaults to `undefined`] |
| **fingerprint** | `string` | Only returns the machine with this exact fingerprint. | [Optional] [Defaults to `undefined`] |
| **status** | `active`, `deactivated` | Only returns the machines with this status. | [Optional] [Defaults to `undefined`] [Enum: active, deactivated] |

### Return type

[**MachineList**](MachineList.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the machines of the license |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

