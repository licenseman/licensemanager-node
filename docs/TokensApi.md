# TokensApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createCustomerToken**](TokensApi.md#createcustomertoken) | **POST** /v1/customers/{id}/tokens | Create a customer token |
| [**createLicenseToken**](TokensApi.md#createlicensetoken) | **POST** /v1/licenses/{id}/tokens | Create a license token |
| [**createMachineToken**](TokensApi.md#createmachinetoken) | **POST** /v1/machines/{id}/tokens | Create a machine token |



## createCustomerToken

> Token createCustomerToken(id, createToken)

Create a customer token

Creates a token scoped to the customer, with the permissions of &#x60;scope&#x60;, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the &#x60;token&#x60; security scheme for what a token reaches.  A token can\&#39;t be revoked: it works until it expires, unless the resource it\&#39;s scoped to is deleted.  **Required role permission**: &#x60;token:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  TokensApi,
} from '@licenseman/sdk';
import type { CreateCustomerTokenRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new TokensApi(config);

  const body = {
    // string
    id: c9Wd3RtE,
    // CreateToken
    createToken: ...,
  } satisfies CreateCustomerTokenRequest;

  try {
    const data = await api.createCustomerToken(body);
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
| **createToken** | [CreateToken](CreateToken.md) |  | |

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created token |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Customer not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createLicenseToken

> Token createLicenseToken(id, createToken)

Create a license token

Creates a token scoped to the license, with the permissions of &#x60;scope&#x60;, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the &#x60;token&#x60; security scheme for what a token reaches.  A token can\&#39;t be revoked: it works until it expires, unless the resource it\&#39;s scoped to is deleted.  **Token access**: customer tokens. A customer token creates tokens for its customer\&#39;s licenses, with the permissions and at most the expiration it has.  **Required role permission**: &#x60;token:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  TokensApi,
} from '@licenseman/sdk';
import type { CreateLicenseTokenRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
    // Configure HTTP bearer authorization: token
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new TokensApi(config);

  const body = {
    // string
    id: c9Wd3RtE,
    // CreateToken
    createToken: ...,
  } satisfies CreateLicenseTokenRequest;

  try {
    const data = await api.createLicenseToken(body);
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
| **createToken** | [CreateToken](CreateToken.md) |  | |

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created token |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createMachineToken

> Token createMachineToken(id, createToken)

Create a machine token

Creates a token scoped to the machine, with the permissions of &#x60;scope&#x60;, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the &#x60;token&#x60; security scheme for what a token reaches.  A token can\&#39;t be revoked: it works until it expires, unless the resource it\&#39;s scoped to is deleted.  **Token access**: customer, license tokens. A customer or license token creates tokens for the machines it reaches, with the permissions and at most the expiration it has.  **Required role permission**: &#x60;token:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  TokensApi,
} from '@licenseman/sdk';
import type { CreateMachineTokenRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
    // Configure HTTP bearer authorization: token
    accessToken: "YOUR BEARER TOKEN",
  });
  const api = new TokensApi(config);

  const body = {
    // string
    id: c9Wd3RtE,
    // CreateToken
    createToken: ...,
  } satisfies CreateMachineTokenRequest;

  try {
    const data = await api.createMachineToken(body);
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
| **createToken** | [CreateToken](CreateToken.md) |  | |

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created token |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Machine not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

