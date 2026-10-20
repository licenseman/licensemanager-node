# IntegrationsApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**checkIntegration**](IntegrationsApi.md#checkintegration) | **POST** /v1/integrations/{id}/check | Check an integration |
| [**connectStripe**](IntegrationsApi.md#connectstripe) | **PUT** /v1/products/{productId}/integrations/stripe | Connect Stripe |
| [**createStripeMapping**](IntegrationsApi.md#createstripemapping) | **POST** /v1/products/{productId}/integrations/stripe/mappings | Map a Stripe price to a policy |
| [**deleteStripeMapping**](IntegrationsApi.md#deletestripemapping) | **DELETE** /v1/integration-mappings/{id} | Delete a mapping |
| [**disconnectIntegration**](IntegrationsApi.md#disconnectintegration) | **DELETE** /v1/integrations/{id} | Disconnect an integration |
| [**getStripeIntegration**](IntegrationsApi.md#getstripeintegration) | **GET** /v1/products/{productId}/integrations/stripe | Get the Stripe integration of a product |
| [**listStripePrices**](IntegrationsApi.md#liststripeprices) | **GET** /v1/integrations/{id}/stripe/prices | List the Stripe prices of an integration |
| [**updateStripeMapping**](IntegrationsApi.md#updatestripemapping) | **PATCH** /v1/integration-mappings/{id} | Change the policy of a mapping |



## checkIntegration

> Integration checkIntegration(id)

Check an integration

Checks right away, as done every day, that the API key still works and can manage the webhook endpoint, which is pointed at the server\&#39;s webhook URL again (or created again when it was deleted). Updates the status. Doesn\&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  IntegrationsApi,
} from '@licenseman/sdk';
import type { CheckIntegrationRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new IntegrationsApi(config);

  const body = {
    // string
    id: i8Fz4QnRt,
  } satisfies CheckIntegrationRequest;

  try {
    const data = await api.checkIntegration(body);
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

[**Integration**](Integration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Checked integration |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Integration not found |  -  |
| **409** | &#x60;webhook_url_unreachable&#x60;: Stripe can\&#39;t reach the server\&#39;s webhook URL |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn\&#39;t be reached |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## connectStripe

> StripeIntegration connectStripe(productId, connectStripe)

Connect Stripe

Connects the Stripe account of the API key for the organization\&#39;s products of the product\&#39;s mode, or replaces the key of the existing connection. Checks the key works and has the required permissions, then creates a webhook endpoint on the account, telling the app about payments. Doesn\&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  IntegrationsApi,
} from '@licenseman/sdk';
import type { ConnectStripeRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new IntegrationsApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // ConnectStripe
    connectStripe: ...,
  } satisfies ConnectStripeRequest;

  try {
    const data = await api.connectStripe(body);
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
| **connectStripe** | [ConnectStripe](ConnectStripe.md) |  | |

### Return type

[**StripeIntegration**](StripeIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stripe integration |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **409** | &#x60;webhook_url_unreachable&#x60;: Stripe can\&#39;t reach the server\&#39;s webhook URL |  -  |
| **422** | &#x60;validation_error&#x60;: invalid body. &#x60;invalid_api_key&#x60;: not a Stripe secret or restricted key, or Stripe rejected it. &#x60;key_mode_mismatch&#x60;: a test mode key for a live product, or the opposite. &#x60;missing_permission&#x60;: the key lacks required permissions, listed in the message |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn\&#39;t be reached |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## createStripeMapping

> IntegrationMapping createStripeMapping(productId, createIntegrationMapping)

Map a Stripe price to a policy

Paying the price then creates licenses of the product with the policy: one per unit bought. Doesn\&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  IntegrationsApi,
} from '@licenseman/sdk';
import type { CreateStripeMappingRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new IntegrationsApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
    // CreateIntegrationMapping
    createIntegrationMapping: ...,
  } satisfies CreateStripeMappingRequest;

  try {
    const data = await api.createStripeMapping(body);
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
| **createIntegrationMapping** | [CreateIntegrationMapping](CreateIntegrationMapping.md) |  | |

### Return type

[**IntegrationMapping**](IntegrationMapping.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created mapping |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | &#x60;not_found&#x60;: product not found. &#x60;policy_not_found&#x60;: the product has no policy with this &#x60;policyId&#x60;. &#x60;price_not_found&#x60;: the Stripe account has no price with this &#x60;stripePriceId&#x60; |  -  |
| **409** | &#x60;not_connected&#x60;: Stripe isn\&#39;t connected in the product\&#39;s mode. &#x60;price_mapped&#x60;: the price already creates licenses of a product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid body. &#x60;price_unusable&#x60;: the price is archived, or isn\&#39;t a one-time price |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn\&#39;t be reached |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteStripeMapping

> deleteStripeMapping(id)

Delete a mapping

Paying the price no longer creates licenses. The licenses it created stay. Doesn\&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  IntegrationsApi,
} from '@licenseman/sdk';
import type { DeleteStripeMappingRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new IntegrationsApi(config);

  const body = {
    // string
    id: i8Fz4QnRt,
  } satisfies DeleteStripeMappingRequest;

  try {
    const data = await api.deleteStripeMapping(body);
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
| **404** | Mapping not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## disconnectIntegration

> disconnectIntegration(id)

Disconnect an integration

Deletes the webhook endpoint from the Stripe account first, then the integration with its mappings, for every product. The endpoint is skipped when it\&#39;s already gone or the key no longer works; otherwise, when it can\&#39;t be deleted, the integration is kept. The licenses it created stay. Revoke the API key in Stripe afterwards. Doesn\&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:delete&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  IntegrationsApi,
} from '@licenseman/sdk';
import type { DisconnectIntegrationRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new IntegrationsApi(config);

  const body = {
    // string
    id: i8Fz4QnRt,
  } satisfies DisconnectIntegrationRequest;

  try {
    const data = await api.disconnectIntegration(body);
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
| **204** | Disconnected |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Integration not found |  -  |
| **422** | &#x60;missing_permission&#x60;: the key can\&#39;t delete the webhook endpoint |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn\&#39;t be reached |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getStripeIntegration

> StripeIntegration getStripeIntegration(productId)

Get the Stripe integration of a product

The organization connects one Stripe account for its live products, and one in test mode for its test products. Its mappings tell which Stripe prices create licenses of the product. Doesn\&#39;t accept tokens: only API keys and sessions.

### Example

```ts
import {
  Configuration,
  IntegrationsApi,
} from '@licenseman/sdk';
import type { GetStripeIntegrationRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new IntegrationsApi(config);

  const body = {
    // string
    productId: x7Kp2QaZ,
  } satisfies GetStripeIntegrationRequest;

  try {
    const data = await api.getStripeIntegration(body);
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

### Return type

[**StripeIntegration**](StripeIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stripe integration |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listStripePrices

> ListStripePrices200Response listStripePrices(id)

List the Stripe prices of an integration

Active one-time prices of active products of the Stripe account, the ones that can be mapped, up to 500. Doesn\&#39;t accept tokens: only API keys and sessions.

### Example

```ts
import {
  Configuration,
  IntegrationsApi,
} from '@licenseman/sdk';
import type { ListStripePricesRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new IntegrationsApi(config);

  const body = {
    // string
    id: i8Fz4QnRt,
  } satisfies ListStripePricesRequest;

  try {
    const data = await api.listStripePrices(body);
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

[**ListStripePrices200Response**](ListStripePrices200Response.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Prices |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Integration not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn\&#39;t be reached, or refused the request |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## updateStripeMapping

> IntegrationMapping updateStripeMapping(id, updateIntegrationMapping)

Change the policy of a mapping

Only affects the licenses created afterwards. Doesn\&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  IntegrationsApi,
} from '@licenseman/sdk';
import type { UpdateStripeMappingRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new IntegrationsApi(config);

  const body = {
    // string
    id: i8Fz4QnRt,
    // UpdateIntegrationMapping
    updateIntegrationMapping: ...,
  } satisfies UpdateStripeMappingRequest;

  try {
    const data = await api.updateStripeMapping(body);
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
| **updateIntegrationMapping** | [UpdateIntegrationMapping](UpdateIntegrationMapping.md) |  | |

### Return type

[**IntegrationMapping**](IntegrationMapping.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated mapping |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | &#x60;not_found&#x60;: mapping not found. &#x60;policy_not_found&#x60;: its product has no policy with this &#x60;policyId&#x60; |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

