# LicenseManager TypeScript SDK

[![npm version](https://img.shields.io/npm/v/@licenseman/sdk)](https://www.npmjs.com/package/@licenseman/sdk)
[![npm downloads](https://img.shields.io/npm/dm/@licenseman/sdk)](https://www.npmjs.com/package/@licenseman/sdk)
[![Types](https://img.shields.io/npm/types/@licenseman/sdk)](https://www.npmjs.com/package/@licenseman/sdk)
[![Publish](https://github.com/licenseman/licensemanager-node/actions/workflows/publish.yml/badge.svg)](https://github.com/licenseman/licensemanager-node/actions/workflows/publish.yml)
[![License](https://img.shields.io/github/license/licenseman/licensemanager-node)](https://github.com/licenseman/licensemanager-node/blob/main/LICENSE)
[![Documentation](https://img.shields.io/badge/docs-licensemanager.dev-blue)](https://licensemanager.dev/docs/sdks/typescript)

The official TypeScript SDK for the [LicenseManager](https://licensemanager.dev) API: issue, manage and validate software licenses. Fully typed, built on `fetch`: works in Node.js, Deno, Bun, edge runtimes and browsers.

**[Documentation](https://licensemanager.dev/docs/sdks/typescript)** · **[API reference](https://api.licensemanager.dev/docs)** · **[Changelog](CHANGELOG.md)**

## Requirements

Node.js 18 or later, or any runtime with `fetch`.

## Installation

```sh
npm install @licenseman/sdk
```

## Usage

Create an API key in the LicenseManager app, then create a license after a sale:

```ts
import { Configuration, LicensesApi } from "@licenseman/sdk";

const licenses = new LicensesApi(
  new Configuration({ apiKey: process.env.LICENSEMANAGER_API_KEY }),
);

const license = await licenses.createLicense({
  productId: "x7Kp2QaZ",
  createLicense: {
    email: "jane@example.com",
  },
});
```

And validate it from your application, which needs no API key:

```ts
import { LicensesApi } from "@licenseman/sdk";

const licenses = new LicensesApi();

const licenseToken = await licenses.validateKey({
  productId: "x7Kp2QaZ",
  validateKey: {
    key: "7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF",
    fingerprint: "4c:32:75:8f:9a:1e",
    version: "1.4.2",
  },
});
```

## Authentication

Most endpoints take an organization API key: keep it on your servers. The endpoints your application calls directly, like validating a key, take no credentials or a token scoped to a customer, license or machine. See [authentication](https://licensemanager.dev/docs/api/authentication) and [scoped tokens](https://licensemanager.dev/docs/api/scoped-tokens).

```ts
import { Configuration } from "@licenseman/sdk";

// With an API key, from your backend:
const configuration = new Configuration({ apiKey: process.env.LICENSEMANAGER_API_KEY });

// With a token scoped to a customer, license or machine:
const scoped = new Configuration({ accessToken: token });
```

## Errors

Failed requests answer an error with a stable `code` to branch on, listed for each endpoint in the [API reference](https://api.licensemanager.dev/docs). See [errors](https://licensemanager.dev/docs/api/errors).

```ts
import { ResponseError } from "@licenseman/sdk";

try {
  await licenses.getLicense({ id: "l3Nv8KwB" });
} catch (error) {
  if (error instanceof ResponseError) {
    const { error: details } = await error.response.json();
    console.error(error.response.status, details.code, details.message);
  }
}
```

## Reference

Every method is documented, with its parameters and responses, in the [`docs`](docs) folder:

| Class | Methods |
| --- | --- |
| [`LicensesApi`](docs/LicensesApi.md) | `validateKey`, `listLicenses`, `createLicense`, `listCustomerLicenses`, `getLicense`, `deleteLicense`, `updateLicense`, `getLicenseStats`, `sendLicenseKeys`, `getSigningKey` |
| [`PortalApi`](docs/PortalApi.md) | `getPortal`, `requestPortalLink`, `createPortalLink`, `sendPortalLink` |
| [`ProductsApi`](docs/ProductsApi.md) | `listProducts`, `createProduct`, `getProduct`, `deleteProduct`, `updateProduct`, `resetProduct`, `uploadProductLogo`, `deleteProductLogo`, `getProductStats` |
| [`PoliciesApi`](docs/PoliciesApi.md) | `listPolicies`, `createPolicy`, `getPolicy`, `deletePolicy`, `updatePolicy` |
| [`CustomersApi`](docs/CustomersApi.md) | `listCustomers`, `createCustomer`, `getCustomer`, `deleteCustomer`, `updateCustomer` |
| [`MachinesApi`](docs/MachinesApi.md) | `listMachines`, `getMachine`, `deactivateMachine` |
| [`ReleasesApi`](docs/ReleasesApi.md) | `listReleases`, `createRelease`, `getRelease`, `deleteRelease`, `updateRelease` |
| [`TokensApi`](docs/TokensApi.md) | `createCustomerToken`, `createLicenseToken`, `createMachineToken` |
| [`EventsApi`](docs/EventsApi.md) | `listPolicyEvents`, `listLicenseEvents` |
| [`IntegrationsApi`](docs/IntegrationsApi.md) | `getStripeIntegration`, `connectStripe`, `disconnectIntegration`, `checkIntegration`, `listStripePrices`, `createStripeMapping`, `deleteStripeMapping`, `updateStripeMapping` |

## Versioning

This SDK follows [semantic versioning](https://semver.org) and is generated from the [OpenAPI document](openapi.json) of the API: each release is listed in the [changelog](CHANGELOG.md). Please don't open pull requests, they would be overwritten by the next release: [open an issue](https://github.com/licenseman/licensemanager-node/issues) instead.

## License

See [LICENSE](LICENSE).
