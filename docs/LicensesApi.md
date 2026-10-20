# LicensesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createLicense**](LicensesApi.md#createlicense) | **POST** /v1/products/{productId}/licenses | Create a license |
| [**deleteLicense**](LicensesApi.md#deletelicense) | **DELETE** /v1/licenses/{id} | Delete a license |
| [**getLicense**](LicensesApi.md#getlicense) | **GET** /v1/licenses/{id} | Get a license |
| [**getLicenseStats**](LicensesApi.md#getlicensestats) | **GET** /v1/licenses/{id}/stats | Get the stats of a license |
| [**getSigningKey**](LicensesApi.md#getsigningkey) | **GET** /v1/signing-key | Get the organization\&#39;s signing key |
| [**listCustomerLicenses**](LicensesApi.md#listcustomerlicenses) | **GET** /v1/customers/{customerId}/licenses | List the licenses of a customer |
| [**listLicenses**](LicensesApi.md#listlicenses) | **GET** /v1/products/{productId}/licenses | List the licenses of a product |
| [**sendLicenseKeys**](LicensesApi.md#sendlicensekeys) | **POST** /v1/licenses/send-keys | Email license keys to their customers |
| [**updateLicense**](LicensesApi.md#updatelicense) | **PATCH** /v1/licenses/{id} | Update a license |
| [**validateKey**](LicensesApi.md#validatekey) | **POST** /v1/products/{productId}/validate-key | Validate a license key |



## createLicense

> License createLicense(productId, createLicense)

Create a license

Without a &#x60;key&#x60;, the license gets a random one, like &#x60;7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF&#x60;: 5 groups of 5 characters separated by dashes, each character an upper case letter or a digit other than &#x60;O&#x60;, &#x60;0&#x60;, &#x60;I&#x60; and &#x60;1&#x60;. That\&#39;s 32 possible characters encoding 5 bits each, for 125 random bits.  Without a &#x60;policyId&#x60;, the license follows the product\&#39;s default policy.  Without an &#x60;expiresAt&#x60;, the license expires after the duration of its policy, or never when the policy has none. &#x60;expiresAt: null&#x60; makes it never expire.  Without a &#x60;price&#x60;, the price paid for the license is unknown: it\&#39;s left out of the revenue stats.  The values of &#x60;maxVersion&#x60; left out are taken from the max version of the policy: its hard-coded version, or the times after the creation of the license its versions lock.  The license belongs to the product\&#39;s customer with the given &#x60;email&#x60;, which is created when there\&#39;s none.  With &#x60;sendKey: true&#x60;, the key is emailed to the customer once the license is created.  The license copies the settings of its policy when it\&#39;s created: later changes to the policy don\&#39;t affect it. Its key, policy and customer can\&#39;t be changed afterwards.  **Required role permission**: &#x60;license:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { CreateLicenseRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new LicensesApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // CreateLicense
    createLicense: ...,
  } satisfies CreateLicenseRequest;

  try {
    const data = await api.createLicense(body);
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
| **createLicense** | [CreateLicense](CreateLicense.md) |  | |

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created license |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | &#x60;not_found&#x60;: product not found. &#x60;policy_not_found&#x60;: the product has no policy with this &#x60;policyId&#x60; |  -  |
| **409** | &#x60;key_taken&#x60;: key already used by another license of the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteLicense

> deleteLicense(id)

Delete a license

Deletes the license along with its deactivated machines. A license used on active machines can\&#39;t be deleted: deactivate them first. The tokens scoped to the license or its machines stop working, but the license tokens &#x60;validateKey&#x60; already returned stay valid until they expire. Its events can no longer be listed.  **Required role permission**: &#x60;license:delete&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { DeleteLicenseRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new LicensesApi(config);

  const body = {
    // string
    id: l3Nv8KwB,
  } satisfies DeleteLicenseRequest;

  try {
    const data = await api.deleteLicense(body);
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
| **404** | License not found |  -  |
| **409** | &#x60;license_in_use&#x60;: the license is used on active machines |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getLicense

> License getLicense(id)

Get a license

**Token access**: customer, license, machine tokens with the &#x60;license:read&#x60; permission (or the matching write one). A token reaches the license it\&#39;s scoped to, the licenses of its customer, or the license of its machine.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { GetLicenseRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
    // Configure HTTP bearer authorization: token
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new LicensesApi(config);

  const body = {
    // string
    id: l3Nv8KwB,
  } satisfies GetLicenseRequest;

  try {
    const data = await api.getLicense(body);
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

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | License |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getLicenseStats

> LicenseStats getLicenseStats(id)

Get the stats of a license

Daily number of successful activations of the license over the last 90 days, today included, per machine and per version of the application. Days are in UTC.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { GetLicenseStatsRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new LicensesApi(config);

  const body = {
    // string
    id: l3Nv8KwB,
  } satisfies GetLicenseStatsRequest;

  try {
    const data = await api.getLicenseStats(body);
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

[**LicenseStats**](LicenseStats.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stats of the license |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getSigningKey

> SigningKey getSigningKey()

Get the organization\&#39;s signing key

Public key verifying the license tokens returned by &#x60;validateKey&#x60;, to embed in applications. Created the first time it\&#39;s needed, and never rotated. The organization has a single key, signing the tokens of its live and test products alike: check the tokens\&#39; &#x60;aud&#x60; to tell them apart.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { GetSigningKeyRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new LicensesApi(config);

  try {
    const data = await api.getSigningKey();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// Run the test
example().catch(console.error);
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**SigningKey**](SigningKey.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Signing key |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listCustomerLicenses

> LicenseList listCustomerLicenses(customerId, page, pageSize, sort, search, key, policyId, machineVersion, status, createdFrom, createdTo, lastActivatedFrom, lastActivatedTo, neverActivated, expiresFrom, expiresTo, neverExpires, currency, price, priceMin, priceMax, hasPrice)

List the licenses of a customer

Sorting by &#x60;lastActivatedAt&#x60; puts the licenses never activated last in both orders. Sorting by &#x60;price&#x60; compares the amounts whatever their currency, and puts the licenses without a price last in both orders.  **Token access**: customer tokens with the &#x60;license:read&#x60; permission (or the matching write one). A customer token reaches its own licenses.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { ListCustomerLicensesRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
    // Configure HTTP bearer authorization: token
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new LicensesApi(config);

  const body = {
    // string
    customerId: c9Wd3RtE,
    // number | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional)
    page: 1,
    // number | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional)
    pageSize: 20,
    // 'key' | '-key' | 'createdAt' | '-createdAt' | 'expiresAt' | '-expiresAt' | 'maxMachines' | '-maxMachines' | 'maxOfflineDurationSeconds' | '-maxOfflineDurationSeconds' | 'lastActivatedAt' | '-lastActivatedAt' | 'lockMajorAt' | '-lockMajorAt' | 'lockMinorAt' | '-lockMinorAt' | 'updatedAt' | '-updatedAt' | 'price' | '-price' | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional)
    sort: -createdAt,
    // string | Case-insensitive text the key contains. (optional)
    search: X9ZPA,
    // string | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`. (optional)
    key: 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF,
    // string | Only returns the licenses following this policy. (optional)
    policyId: p4Rt8LmQ,
    // string | Only returns the licenses with at least one active machine running this version of the product. (optional)
    machineVersion: 2.3.1,
    // LicenseStatus | Only returns the licenses with this status. (optional)
    status: ...,
    // Date | Only returns the licenses created at or after this date. (optional)
    createdFrom: 2026-01-01T00:00:00.000Z,
    // Date | Only returns the licenses created at or before this date. (optional)
    createdTo: 2026-02-01T00:00:00.000Z,
    // Date | Only returns the licenses last activated at or after this date. Licenses never activated are left out. (optional)
    lastActivatedFrom: 2026-01-01T00:00:00.000Z,
    // Date | Only returns the licenses last activated at or before this date. Licenses never activated are left out. (optional)
    lastActivatedTo: 2026-02-01T00:00:00.000Z,
    // 'true' | 'false' | `true` only returns the licenses never activated, `false` only the ones activated at least once. (optional)
    neverActivated: true,
    // Date | Only returns the licenses expiring at or after this date. Licenses that never expire are left out. (optional)
    expiresFrom: 2026-01-01T00:00:00.000Z,
    // Date | Only returns the licenses expiring at or before this date. Licenses that never expire are left out. (optional)
    expiresTo: 2026-02-01T00:00:00.000Z,
    // 'true' | 'false' | `true` only returns the licenses that never expire, `false` only the ones with an expiration date. (optional)
    neverExpires: true,
    // string | Only returns the licenses paid in this currency. (optional)
    currency: USD,
    // number | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    price: 49.99,
    // number | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    priceMin: 49.99,
    // number | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    priceMax: 49.99,
    // 'true' | 'false' | `true` only returns the licenses with a price, `false` only the ones without. (optional)
    hasPrice: true,
  } satisfies ListCustomerLicensesRequest;

  try {
    const data = await api.listCustomerLicenses(body);
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
| **customerId** | `string` |  | [Defaults to `undefined`] |
| **page** | `number` | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [Optional] [Defaults to `1`] |
| **pageSize** | `number` | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [Optional] [Defaults to `20`] |
| **sort** | `key`, `-key`, `createdAt`, `-createdAt`, `expiresAt`, `-expiresAt`, `maxMachines`, `-maxMachines`, `maxOfflineDurationSeconds`, `-maxOfflineDurationSeconds`, `lastActivatedAt`, `-lastActivatedAt`, `lockMajorAt`, `-lockMajorAt`, `lockMinorAt`, `-lockMinorAt`, `updatedAt`, `-updatedAt`, `price`, `-price` | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [Optional] [Defaults to `&#39;-createdAt&#39;`] [Enum: key, -key, createdAt, -createdAt, expiresAt, -expiresAt, maxMachines, -maxMachines, maxOfflineDurationSeconds, -maxOfflineDurationSeconds, lastActivatedAt, -lastActivatedAt, lockMajorAt, -lockMajorAt, lockMinorAt, -lockMinorAt, updatedAt, -updatedAt, price, -price] |
| **search** | `string` | Case-insensitive text the key contains. | [Optional] [Defaults to `undefined`] |
| **key** | `string` | Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [Optional] [Defaults to `undefined`] |
| **policyId** | `string` | Only returns the licenses following this policy. | [Optional] [Defaults to `undefined`] |
| **machineVersion** | `string` | Only returns the licenses with at least one active machine running this version of the product. | [Optional] [Defaults to `undefined`] |
| **status** | `LicenseStatus` | Only returns the licenses with this status. | [Optional] [Defaults to `undefined`] [Enum: active, inactive, expired] |
| **createdFrom** | `Date` | Only returns the licenses created at or after this date. | [Optional] [Defaults to `undefined`] |
| **createdTo** | `Date` | Only returns the licenses created at or before this date. | [Optional] [Defaults to `undefined`] |
| **lastActivatedFrom** | `Date` | Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [Optional] [Defaults to `undefined`] |
| **lastActivatedTo** | `Date` | Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [Optional] [Defaults to `undefined`] |
| **neverActivated** | `true`, `false` | &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [Optional] [Defaults to `undefined`] [Enum: true, false] |
| **expiresFrom** | `Date` | Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [Optional] [Defaults to `undefined`] |
| **expiresTo** | `Date` | Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [Optional] [Defaults to `undefined`] |
| **neverExpires** | `true`, `false` | &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [Optional] [Defaults to `undefined`] [Enum: true, false] |
| **currency** | `string` | Only returns the licenses paid in this currency. | [Optional] [Defaults to `undefined`] |
| **price** | `number` | Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [Optional] [Defaults to `undefined`] |
| **priceMin** | `number` | Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [Optional] [Defaults to `undefined`] |
| **priceMax** | `number` | Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [Optional] [Defaults to `undefined`] |
| **hasPrice** | `true`, `false` | &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [Optional] [Defaults to `undefined`] [Enum: true, false] |

### Return type

[**LicenseList**](LicenseList.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the licenses of the customer |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Customer not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listLicenses

> LicenseList listLicenses(productId, page, pageSize, sort, search, key, policyId, customerId, machineVersion, status, createdFrom, createdTo, lastActivatedFrom, lastActivatedTo, neverActivated, expiresFrom, expiresTo, neverExpires, currency, price, priceMin, priceMax, hasPrice)

List the licenses of a product

Sorting by &#x60;lastActivatedAt&#x60; puts the licenses never activated last in both orders. Sorting by &#x60;price&#x60; compares the amounts whatever their currency, and puts the licenses without a price last in both orders.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { ListLicensesRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new LicensesApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // number | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional)
    page: 1,
    // number | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional)
    pageSize: 20,
    // 'key' | '-key' | 'createdAt' | '-createdAt' | 'expiresAt' | '-expiresAt' | 'maxMachines' | '-maxMachines' | 'maxOfflineDurationSeconds' | '-maxOfflineDurationSeconds' | 'lastActivatedAt' | '-lastActivatedAt' | 'lockMajorAt' | '-lockMajorAt' | 'lockMinorAt' | '-lockMinorAt' | 'updatedAt' | '-updatedAt' | 'price' | '-price' | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional)
    sort: -createdAt,
    // string | Case-insensitive text the key contains. (optional)
    search: X9ZPA,
    // string | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`. (optional)
    key: 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF,
    // string | Only returns the licenses following this policy. (optional)
    policyId: p4Rt8LmQ,
    // string | Only returns the licenses of this customer. (optional)
    customerId: c9Wd3RtE,
    // string | Only returns the licenses with at least one active machine running this version of the product. (optional)
    machineVersion: 2.3.1,
    // LicenseStatus | Only returns the licenses with this status. (optional)
    status: ...,
    // Date | Only returns the licenses created at or after this date. (optional)
    createdFrom: 2026-01-01T00:00:00.000Z,
    // Date | Only returns the licenses created at or before this date. (optional)
    createdTo: 2026-02-01T00:00:00.000Z,
    // Date | Only returns the licenses last activated at or after this date. Licenses never activated are left out. (optional)
    lastActivatedFrom: 2026-01-01T00:00:00.000Z,
    // Date | Only returns the licenses last activated at or before this date. Licenses never activated are left out. (optional)
    lastActivatedTo: 2026-02-01T00:00:00.000Z,
    // 'true' | 'false' | `true` only returns the licenses never activated, `false` only the ones activated at least once. (optional)
    neverActivated: true,
    // Date | Only returns the licenses expiring at or after this date. Licenses that never expire are left out. (optional)
    expiresFrom: 2026-01-01T00:00:00.000Z,
    // Date | Only returns the licenses expiring at or before this date. Licenses that never expire are left out. (optional)
    expiresTo: 2026-02-01T00:00:00.000Z,
    // 'true' | 'false' | `true` only returns the licenses that never expire, `false` only the ones with an expiration date. (optional)
    neverExpires: true,
    // string | Only returns the licenses paid in this currency. (optional)
    currency: USD,
    // number | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    price: 49.99,
    // number | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    priceMin: 49.99,
    // number | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    priceMax: 49.99,
    // 'true' | 'false' | `true` only returns the licenses with a price, `false` only the ones without. (optional)
    hasPrice: true,
  } satisfies ListLicensesRequest;

  try {
    const data = await api.listLicenses(body);
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
| **sort** | `key`, `-key`, `createdAt`, `-createdAt`, `expiresAt`, `-expiresAt`, `maxMachines`, `-maxMachines`, `maxOfflineDurationSeconds`, `-maxOfflineDurationSeconds`, `lastActivatedAt`, `-lastActivatedAt`, `lockMajorAt`, `-lockMajorAt`, `lockMinorAt`, `-lockMinorAt`, `updatedAt`, `-updatedAt`, `price`, `-price` | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [Optional] [Defaults to `&#39;-createdAt&#39;`] [Enum: key, -key, createdAt, -createdAt, expiresAt, -expiresAt, maxMachines, -maxMachines, maxOfflineDurationSeconds, -maxOfflineDurationSeconds, lastActivatedAt, -lastActivatedAt, lockMajorAt, -lockMajorAt, lockMinorAt, -lockMinorAt, updatedAt, -updatedAt, price, -price] |
| **search** | `string` | Case-insensitive text the key contains. | [Optional] [Defaults to `undefined`] |
| **key** | `string` | Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [Optional] [Defaults to `undefined`] |
| **policyId** | `string` | Only returns the licenses following this policy. | [Optional] [Defaults to `undefined`] |
| **customerId** | `string` | Only returns the licenses of this customer. | [Optional] [Defaults to `undefined`] |
| **machineVersion** | `string` | Only returns the licenses with at least one active machine running this version of the product. | [Optional] [Defaults to `undefined`] |
| **status** | `LicenseStatus` | Only returns the licenses with this status. | [Optional] [Defaults to `undefined`] [Enum: active, inactive, expired] |
| **createdFrom** | `Date` | Only returns the licenses created at or after this date. | [Optional] [Defaults to `undefined`] |
| **createdTo** | `Date` | Only returns the licenses created at or before this date. | [Optional] [Defaults to `undefined`] |
| **lastActivatedFrom** | `Date` | Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [Optional] [Defaults to `undefined`] |
| **lastActivatedTo** | `Date` | Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [Optional] [Defaults to `undefined`] |
| **neverActivated** | `true`, `false` | &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [Optional] [Defaults to `undefined`] [Enum: true, false] |
| **expiresFrom** | `Date` | Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [Optional] [Defaults to `undefined`] |
| **expiresTo** | `Date` | Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [Optional] [Defaults to `undefined`] |
| **neverExpires** | `true`, `false` | &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [Optional] [Defaults to `undefined`] [Enum: true, false] |
| **currency** | `string` | Only returns the licenses paid in this currency. | [Optional] [Defaults to `undefined`] |
| **price** | `number` | Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [Optional] [Defaults to `undefined`] |
| **priceMin** | `number` | Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [Optional] [Defaults to `undefined`] |
| **priceMax** | `number` | Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [Optional] [Defaults to `undefined`] |
| **hasPrice** | `true`, `false` | &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [Optional] [Defaults to `undefined`] [Enum: true, false] |

### Return type

[**LicenseList**](LicenseList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the licenses of the product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## sendLicenseKeys

> sendLicenseKeys(sendLicenseKeys)

Email license keys to their customers

Emails each customer the keys of its licenses among &#x60;ids&#x60;, with their expiration date: one email per customer, whatever their number of licenses. The licenses can belong to different products of the organization.  Test products only email the members of the organization, so testing never emails real customers: nothing is sent when a license of a test product belongs to a customer whose email isn\&#39;t a member\&#39;s.  **Required role permission**: &#x60;license:send&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { SendLicenseKeysRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new LicensesApi(config);

  const body = {
    // SendLicenseKeys
    sendLicenseKeys: ...,
  } satisfies SendLicenseKeysRequest;

  try {
    const data = await api.sendLicenseKeys(body);
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
| **sendLicenseKeys** | [SendLicenseKeys](SendLicenseKeys.md) |  | |

### Return type

`void` (Empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Keys emailed |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | &#x60;not_found&#x60;: one of the licenses wasn\&#39;t found |  -  |
| **409** | &#x60;test_recipient_not_member&#x60;: a license of a test product belongs to a customer whose email isn\&#39;t a member\&#39;s of the organization |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## updateLicense

> License updateLicense(id, updateLicense)

Update a license

The key, policy and customer of a license can\&#39;t be changed: sending them does nothing.  The changes apply to the next validations of the key, not to the license tokens &#x60;validateKey&#x60; already returned, which stay valid until they expire. Lowering &#x60;maxMachines&#x60; doesn\&#39;t deactivate machines: the ones already active keep validating, and new ones are refused until enough are deactivated.  **Required role permission**: &#x60;license:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { UpdateLicenseRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new LicensesApi(config);

  const body = {
    // string
    id: l3Nv8KwB,
    // UpdateLicense
    updateLicense: ...,
  } satisfies UpdateLicenseRequest;

  try {
    const data = await api.updateLicense(body);
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
| **updateLicense** | [UpdateLicense](UpdateLicense.md) |  | |

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated license |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## validateKey

> LicenseToken validateKey(productId, validateKey)

Validate a license key

Checks the license key of the product on a machine and returns a token the application can verify offline with the organization\&#39;s public key. Doesn\&#39;t need authentication.  The license must allow the &#x60;version&#x60;: up to its &#x60;maxVersion.version&#x60; when it has one, like &#x60;\&quot;2.3\&quot;&#x60; for every 2.3.z version and older. Its &#x60;maxVersion.lockMajorAt&#x60; and &#x60;maxVersion.lockMinorAt&#x60; are enforced once they hard-code &#x60;maxVersion.version&#x60;, within the hour they\&#39;re reached. When it doesn\&#39;t, the error\&#39;s &#x60;latestAllowedVersion&#x60; is the latest release of the product the license allows, so the application can offer to install it.  The machine with the &#x60;fingerprint&#x60; is created when the license has none, and activated when it\&#39;s deactivated, unless the license is already active on its maximum number of machines. A machine that\&#39;s already active is never refused for the maximum number of machines, even when it was lowered below the number of active machines. Its &#x60;version&#x60;, and its &#x60;name&#x60; and &#x60;platform&#x60; when given, are updated: they can\&#39;t be cleared.  The checks run in this order, and the first one failing answers: the license has expired, then it doesn\&#39;t allow the version, then it\&#39;s on its maximum number of machines. Each failure is recorded as a &#x60;license.validation_failed&#x60; event, except for keys that don\&#39;t exist.  Changes to the license, like deactivating the machine or shortening its expiration, don\&#39;t revoke the tokens already returned: the application only sees them when it validates its key again, at the latest when its token expires.

### Example

```ts
import {
  Configuration,
  LicensesApi,
} from '@licenseman/sdk';
import type { ValidateKeyRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const api = new LicensesApi();

  const body = {
    // string
    productId: x7Kp2QaZ,
    // ValidateKey
    validateKey: ...,
  } satisfies ValidateKeyRequest;

  try {
    const data = await api.validateKey(body);
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
| **validateKey** | [ValidateKey](ValidateKey.md) |  | |

### Return type

[**LicenseToken**](LicenseToken.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Signed license token |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period |  -  |
| **403** | &#x60;license_expired&#x60;: the license has expired. &#x60;version_not_allowed&#x60;: the license doesn\&#39;t allow the version, with the &#x60;latestAllowedVersion&#x60;. &#x60;machine_limit_reached&#x60;: the license is already active on its maximum number of machines |  -  |
| **404** | &#x60;not_found&#x60;: the product doesn\&#39;t exist, or has no license with this key |  -  |
| **422** | &#x60;validation_error&#x60;: invalid body |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

