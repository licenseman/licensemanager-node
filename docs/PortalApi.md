# PortalApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createPortalLink**](PortalApi.md#createportallink) | **POST** /v1/customers/{id}/portal-links | Create a link to the customer portal |
| [**getPortal**](PortalApi.md#getportal) | **GET** /v1/portal/{productId} | Get the customer portal of a product |
| [**requestPortalLink**](PortalApi.md#requestportallink) | **POST** /v1/portal/{productId}/request-link | Email a link to the customer portal |
| [**sendPortalLink**](PortalApi.md#sendportallink) | **POST** /v1/customers/{id}/portal-links/send | Email a link to the customer portal to the customer |



## createPortalLink

> PortalLink createPortalLink(id, createPortalLink)

Create a link to the customer portal

Link letting the customer see their licenses and deactivate their machines in the customer portal, without signing in. Anyone with the link can, until it expires or the customer is deleted: it can\&#39;t be revoked otherwise. The token also works with the API endpoints that accept customer tokens.  Links can be created while the product\&#39;s customer portal is disabled, but the portal answers &#x60;404&#x60; until it\&#39;s enabled, and &#x60;sendPortalLink&#x60; refuses to email them.  **Required role permission**: &#x60;portalLink:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  PortalApi,
} from '@licenseman/sdk';
import type { CreatePortalLinkRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new PortalApi(config);

  const body = {
    // string
    id: c9Wd3RtE,
    // CreatePortalLink
    createPortalLink: ...,
  } satisfies CreatePortalLinkRequest;

  try {
    const data = await api.createPortalLink(body);
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
| **createPortalLink** | [CreatePortalLink](CreatePortalLink.md) |  | |

### Return type

[**PortalLink**](PortalLink.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created link |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Customer not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getPortal

> Portal getPortal(productId, returnUrl)

Get the customer portal of a product

Names of the product and of its organization, colors of the customer portal, and link back to the product\&#39;s website. Answers &#x60;404&#x60; when the product\&#39;s customer portal is disabled: with the &#x60;portal_disabled&#x60; code and the slugs of the product and its organization when signed in as a member of the organization, so they can enable it. Doesn\&#39;t need authentication.

### Example

```ts
import {
  Configuration,
  PortalApi,
} from '@licenseman/sdk';
import type { GetPortalRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const api = new PortalApi();

  const body = {
    // string
    productId: x7Kp2QaZ,
    // string | Link back to your website to show, used when its domain is one of the product\'s `returnDomains`. (optional)
    returnUrl: https://example.com/account,
  } satisfies GetPortalRequest;

  try {
    const data = await api.getPortal(body);
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
| **returnUrl** | `string` | Link back to your website to show, used when its domain is one of the product\&#39;s &#x60;returnDomains&#x60;. | [Optional] [Defaults to `undefined`] |

### Return type

[**Portal**](Portal.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Customer portal |  -  |
| **404** | &#x60;not_found&#x60;: product not found, or its customer portal is disabled. &#x60;portal_disabled&#x60;: its customer portal is disabled, for members of its organization |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## requestPortalLink

> requestPortalLink(productId, requestPortalLink)

Email a link to the customer portal

Emails the customer of the product with this email a link to the customer portal, working for 1 hour. Answers &#x60;404&#x60; when the product\&#39;s customer portal is disabled. Answers the same whether the customer exists or not, so the API doesn\&#39;t tell which emails are customers. Test products only email the members of the organization: the link isn\&#39;t sent to other customers, with the same answer. Doesn\&#39;t need authentication.

### Example

```ts
import {
  Configuration,
  PortalApi,
} from '@licenseman/sdk';
import type { RequestPortalLinkRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const api = new PortalApi();

  const body = {
    // string
    productId: x7Kp2QaZ,
    // RequestPortalLink
    requestPortalLink: ...,
  } satisfies RequestPortalLinkRequest;

  try {
    const data = await api.requestPortalLink(body);
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
| **requestPortalLink** | [RequestPortalLink](RequestPortalLink.md) |  | |

### Return type

`void` (Empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Link emailed, if the customer exists |  -  |
| **404** | &#x60;not_found&#x60;: product not found, or its customer portal is disabled |  -  |
| **422** | Validation error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## sendPortalLink

> sendPortalLink(id, sendPortalLink)

Email a link to the customer portal to the customer

Emails a link created with &#x60;createPortalLink&#x60; to the customer\&#39;s email. Fails while the product\&#39;s customer portal is disabled, and, in test products, when the customer\&#39;s email isn\&#39;t a member\&#39;s of the organization: test products only email members, so testing never emails real customers.  **Required role permission**: &#x60;portalLink:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  PortalApi,
} from '@licenseman/sdk';
import type { SendPortalLinkRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new PortalApi(config);

  const body = {
    // string
    id: c9Wd3RtE,
    // SendPortalLink
    sendPortalLink: ...,
  } satisfies SendPortalLinkRequest;

  try {
    const data = await api.sendPortalLink(body);
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
| **sendPortalLink** | [SendPortalLink](SendPortalLink.md) |  | |

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
| **204** | Link emailed |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Customer not found |  -  |
| **409** | &#x60;portal_disabled&#x60;: the product\&#39;s customer portal is disabled. &#x60;test_recipient_not_member&#x60;: the product is a test product, and the customer\&#39;s email isn\&#39;t a member\&#39;s of the organization |  -  |
| **422** | &#x60;validation_error&#x60;: invalid body. &#x60;invalid_token&#x60;: the token isn\&#39;t valid, has expired, or isn\&#39;t a customer token of this customer |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

