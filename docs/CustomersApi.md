# CustomersApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createCustomer**](CustomersApi.md#createcustomer) | **POST** /v1/products/{productId}/customers | Create a customer |
| [**deleteCustomer**](CustomersApi.md#deletecustomer) | **DELETE** /v1/customers/{id} | Delete a customer |
| [**getCustomer**](CustomersApi.md#getcustomer) | **GET** /v1/customers/{id} | Get a customer |
| [**listCustomers**](CustomersApi.md#listcustomers) | **GET** /v1/products/{productId}/customers | List the customers of a product |
| [**updateCustomer**](CustomersApi.md#updatecustomer) | **PATCH** /v1/customers/{id} | Update a customer |



## createCustomer

> Customer createCustomer(productId, createCustomer)

Create a customer

**Required role permission**: &#x60;customer:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  CustomersApi,
} from '@licenseman/sdk';
import type { CreateCustomerRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new CustomersApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // CreateCustomer
    createCustomer: ...,
  } satisfies CreateCustomerRequest;

  try {
    const data = await api.createCustomer(body);
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
| **createCustomer** | [CreateCustomer](CreateCustomer.md) |  | |

### Return type

[**Customer**](Customer.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created customer |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **409** | &#x60;email_taken&#x60;: email already used by another customer of the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteCustomer

> deleteCustomer(id)

Delete a customer

A customer that licenses belong to can\&#39;t be deleted: delete them first. The customer tokens of the customer, like the ones of its portal links, stop working.  **Required role permission**: &#x60;customer:delete&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  CustomersApi,
} from '@licenseman/sdk';
import type { DeleteCustomerRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new CustomersApi(config);

  const body = {
    // string
    id: c9Wd3RtE,
  } satisfies DeleteCustomerRequest;

  try {
    const data = await api.deleteCustomer(body);
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
| **404** | Customer not found |  -  |
| **409** | &#x60;customer_in_use&#x60;: licenses belong to the customer |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getCustomer

> Customer getCustomer(id)

Get a customer

**Token access**: customer, license, machine tokens with the &#x60;customer:read&#x60; permission (or the matching write one). A token reaches the customer it\&#39;s scoped to, or the customer of its license or machine.

### Example

```ts
import {
  Configuration,
  CustomersApi,
} from '@licenseman/sdk';
import type { GetCustomerRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
    // Configure HTTP bearer authorization: token
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new CustomersApi(config);

  const body = {
    // string
    id: c9Wd3RtE,
  } satisfies GetCustomerRequest;

  try {
    const data = await api.getCustomer(body);
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

[**Customer**](Customer.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Customer |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Customer not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listCustomers

> CustomerList listCustomers(productId, page, pageSize, sort, search, email)

List the customers of a product

Sorting by &#x60;name&#x60; puts the customers without a name last in both orders.

### Example

```ts
import {
  Configuration,
  CustomersApi,
} from '@licenseman/sdk';
import type { ListCustomersRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new CustomersApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // number | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional)
    page: 1,
    // number | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional)
    pageSize: 20,
    // 'name' | '-name' | 'email' | '-email' | 'licenseCount' | '-licenseCount' | 'createdAt' | '-createdAt' | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional)
    sort: -createdAt,
    // string | Case-insensitive text the name or email contains. (optional)
    search: example.com,
    // string | Only returns the customer with this email, compared regardless of case. (optional)
    email: jane@example.com,
  } satisfies ListCustomersRequest;

  try {
    const data = await api.listCustomers(body);
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
| **sort** | `name`, `-name`, `email`, `-email`, `licenseCount`, `-licenseCount`, `createdAt`, `-createdAt` | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [Optional] [Defaults to `&#39;-createdAt&#39;`] [Enum: name, -name, email, -email, licenseCount, -licenseCount, createdAt, -createdAt] |
| **search** | `string` | Case-insensitive text the name or email contains. | [Optional] [Defaults to `undefined`] |
| **email** | `string` | Only returns the customer with this email, compared regardless of case. | [Optional] [Defaults to `undefined`] |

### Return type

[**CustomerList**](CustomerList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the customers of the product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## updateCustomer

> Customer updateCustomer(id, updateCustomer)

Update a customer

**Required role permission**: &#x60;customer:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  CustomersApi,
} from '@licenseman/sdk';
import type { UpdateCustomerRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new CustomersApi(config);

  const body = {
    // string
    id: c9Wd3RtE,
    // UpdateCustomer
    updateCustomer: ...,
  } satisfies UpdateCustomerRequest;

  try {
    const data = await api.updateCustomer(body);
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
| **updateCustomer** | [UpdateCustomer](UpdateCustomer.md) |  | |

### Return type

[**Customer**](Customer.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated customer |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Customer not found |  -  |
| **409** | &#x60;email_taken&#x60;: email already used by another customer of the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

