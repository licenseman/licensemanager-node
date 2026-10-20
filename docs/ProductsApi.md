# ProductsApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createProduct**](ProductsApi.md#createproduct) | **POST** /v1/products | Create a product |
| [**deleteProduct**](ProductsApi.md#deleteproduct) | **DELETE** /v1/products/{id} | Delete a product |
| [**deleteProductLogo**](ProductsApi.md#deleteproductlogo) | **DELETE** /v1/products/{id}/logo | Delete a product logo |
| [**getProduct**](ProductsApi.md#getproduct) | **GET** /v1/products/{id} | Get a product |
| [**getProductStats**](ProductsApi.md#getproductstats) | **GET** /v1/products/{id}/stats | Get the stats of a product |
| [**listProducts**](ProductsApi.md#listproducts) | **GET** /v1/products | List products |
| [**resetProduct**](ProductsApi.md#resetproduct) | **POST** /v1/products/{id}/reset | Reset a test product |
| [**updateProduct**](ProductsApi.md#updateproduct) | **PATCH** /v1/products/{id} | Update a product |
| [**uploadProductLogo**](ProductsApi.md#uploadproductlogo) | **PUT** /v1/products/{id}/logo | Upload a product logo |



## createProduct

> Product createProduct(createProductWithPolicy)

Create a product

Without a &#x60;slug&#x60;, the product gets one derived from its name: lower cased, without accents and special characters (&#x60;Élan Pro 2!&#x60; becomes &#x60;elan-pro-2&#x60;). When another product of the organization already uses it, a dash and 3 random lowercase letters or digits are appended (&#x60;elan-pro-2-k3f&#x60;), until the slug is free.  An explicit &#x60;slug&#x60; is used as is: the request fails with a &#x60;409&#x60; when it\&#39;s taken, it\&#39;s never changed.  Slug uniqueness is enforced by the database, so when concurrent requests end up with the same slug, only one succeeds and the others get a &#x60;409&#x60;, even without an explicit &#x60;slug&#x60;. Retrying such a request without a &#x60;slug&#x60; derives a new one.  The product is created with its default policy, named &#x60;Default policy&#x60; with the &#x60;default&#x60; slug, whose settings are given by &#x60;defaultPolicy&#x60;. Omitted settings default to licenses that never expire, on a single machine, offline for one week, for every version of the product. Unlike &#x60;createPolicy&#x60;, where &#x60;maxMachines&#x60; defaults to no limit.  With &#x60;isTestFromProductId&#x60;, the product is a test product: its id, its slug, and the ids, slugs and license keys of its resources start with &#x60;test_&#x60; (&#x60;TEST-&#x60; for license keys), and only test API keys reach it. It starts with copies of the policies, releases and portal settings of the live product, &#x60;defaultPolicy&#x60; is ignored. Later changes to the live product aren\&#39;t copied: reset the test product to copy them again. Test API keys can only create test products, live API keys only live ones.  **Required role permission**: &#x60;product:create&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { CreateProductRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // CreateProductWithPolicy
    createProductWithPolicy: ...,
  } satisfies CreateProductRequest;

  try {
    const data = await api.createProduct(body);
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
| **createProductWithPolicy** | [CreateProductWithPolicy](CreateProductWithPolicy.md) |  | |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;api_key_mode&#x60;: the API key\&#39;s mode doesn\&#39;t match the product\&#39;s: test keys only create test products, live keys only live ones |  -  |
| **404** | &#x60;not_found&#x60;: &#x60;isTestFromProductId&#x60; isn\&#39;t a live product of the organization |  -  |
| **409** | &#x60;slug_taken&#x60;: the explicit slug is already used by another product of the organization, or a concurrent request took the same slug first |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteProduct

> deleteProduct(id)

Delete a product

Deletes the product along with its policies, customers and releases, and its test products with everything they hold. A live product that licenses belong to can\&#39;t be deleted: delete them first. A test product can always be deleted, along with its licenses and machines. The events of the deleted policies and licenses can no longer be listed.  **Required role permission**: &#x60;product:delete&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { DeleteProductRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // string
    id: x7Kp2QaZ,
  } satisfies DeleteProductRequest;

  try {
    const data = await api.deleteProduct(body);
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
| **404** | Product not found |  -  |
| **409** | &#x60;product_in_use&#x60;: licenses belong to the live product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## deleteProductLogo

> Product deleteProductLogo(id)

Delete a product logo

Removes the logo of the product, and deletes its image. Succeeds when the product has no logo.  **Required role permission**: &#x60;product:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { DeleteProductLogoRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // string
    id: x7Kp2QaZ,
  } satisfies DeleteProductLogoRequest;

  try {
    const data = await api.deleteProductLogo(body);
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

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Product without a logo |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getProduct

> Product getProduct(id)

Get a product

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { GetProductRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // string
    id: x7Kp2QaZ,
  } satisfies GetProductRequest;

  try {
    const data = await api.getProduct(body);
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

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## getProductStats

> ProductStats getProductStats(id)

Get the stats of a product

Counts of the licenses and machines of the product, number of licenses created each day over the last 30 days and each month over the last 12 months, overall and per policy, revenue per currency over the same periods, and successful activations each day over the last 30 days. Days and months are in UTC.

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { GetProductStatsRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // string
    id: x7Kp2QaZ,
  } satisfies GetProductStatsRequest;

  try {
    const data = await api.getProductStats(body);
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

[**ProductStats**](ProductStats.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stats of the product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## listProducts

> ProductList listProducts(page, pageSize, sort, search, slug, isTest)

List products

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { ListProductsRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // number | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional)
    page: 1,
    // number | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional)
    pageSize: 20,
    // 'name' | '-name' | 'slug' | '-slug' | 'createdAt' | '-createdAt' | 'updatedAt' | '-updatedAt' | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional)
    sort: -createdAt,
    // string | Case-insensitive text the name or slug contains. (optional)
    search: pro,
    // string | Only returns the product with this exact slug. (optional)
    slug: acme-pro,
    // 'true' | 'false' | Only returns the test products with `true`, the live ones with `false`. API keys only list the products of their own mode. (optional)
    isTest: false,
  } satisfies ListProductsRequest;

  try {
    const data = await api.listProducts(body);
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
| **page** | `number` | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [Optional] [Defaults to `1`] |
| **pageSize** | `number` | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [Optional] [Defaults to `20`] |
| **sort** | `name`, `-name`, `slug`, `-slug`, `createdAt`, `-createdAt`, `updatedAt`, `-updatedAt` | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [Optional] [Defaults to `&#39;-createdAt&#39;`] [Enum: name, -name, slug, -slug, createdAt, -createdAt, updatedAt, -updatedAt] |
| **search** | `string` | Case-insensitive text the name or slug contains. | [Optional] [Defaults to `undefined`] |
| **slug** | `string` | Only returns the product with this exact slug. | [Optional] [Defaults to `undefined`] |
| **isTest** | `true`, `false` | Only returns the test products with &#x60;true&#x60;, the live ones with &#x60;false&#x60;. API keys only list the products of their own mode. | [Optional] [Defaults to `undefined`] [Enum: true, false] |

### Return type

[**ProductList**](ProductList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the products of the organization |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## resetProduct

> Product resetProduct(id)

Reset a test product

Deletes the customers, licenses, machines, policies and releases of the test product, with their events, then copies the policies, releases and portal settings of its live product again. Its id, name and slug are kept, but the copied policies get new ids. The tokens of its customers, licenses and machines stop working.  **Required role permission**: &#x60;product:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { ResetProductRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // string
    id: x7Kp2QaZ,
  } satisfies ResetProductRequest;

  try {
    const data = await api.resetProduct(body);
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

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Reset product |  -  |
| **400** | &#x60;not_test_product&#x60;: the product is a live product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## updateProduct

> Product updateProduct(id, updateProduct)

Update a product

A product can\&#39;t be turned into a test product, or back: &#x60;isTestFromProductId&#x60; can\&#39;t be changed.  **Required role permission**: &#x60;product:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { UpdateProductRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // string
    id: x7Kp2QaZ,
    // UpdateProduct
    updateProduct: ...,
  } satisfies UpdateProductRequest;

  try {
    const data = await api.updateProduct(body);
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
| **updateProduct** | [UpdateProduct](UpdateProduct.md) |  | |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **409** | &#x60;slug_taken&#x60;: slug already used by another product of the organization |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)


## uploadProductLogo

> Product uploadProductLogo(id, file)

Upload a product logo

Replaces the logo of the product, shown in the web app and the customer portal. The previous logo is deleted.  Accepts WebP, PNG, JPEG and SVG images up to 1 MB, recognized by their content. Logos are shown in squares: use square images, 256×256 pixels for bitmaps. The web app crops and resizes images to this size, and converts them to WebP, before uploading them.  **Required role permission**: &#x60;product:update&#x60; when called with a session, granted by the member\&#39;s role. API keys aren\&#39;t limited by roles.

### Example

```ts
import {
  Configuration,
  ProductsApi,
} from '@licenseman/sdk';
import type { UploadProductLogoRequest } from '@licenseman/sdk';

async function example() {
  console.log("🚀 Testing @licenseman/sdk SDK...");
  const config = new Configuration({ 
    // To configure API key authorization: apiKey
    apiKey: "YOUR API KEY",
  });
  const api = new ProductsApi(config);

  const body = {
    // string
    id: x7Kp2QaZ,
    // Blob | WebP, PNG, JPEG or SVG image, up to 1 MB.
    file: BINARY_DATA_HERE,
  } satisfies UploadProductLogoRequest;

  try {
    const data = await api.uploadProductLogo(body);
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
| **file** | `Blob` | WebP, PNG, JPEG or SVG image, up to 1 MB. | [Defaults to `undefined`] |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Product with its new logo |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn\&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token\&#39;s signature is invalid, it has expired, or the resource it\&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan\&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan\&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn\&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn\&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **413** | &#x60;logo_too_large&#x60;: the image is larger than 1 MB |  -  |
| **415** | &#x60;unsupported_logo_type&#x60;: the file isn\&#39;t a WebP, PNG, JPEG or SVG image |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#api-endpoints) [[Back to Model list]](../README.md#models) [[Back to README]](../README.md)

