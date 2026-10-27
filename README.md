# LicenseManager PHP SDK

[![Packagist version](https://img.shields.io/packagist/v/lman/sdk)](https://packagist.org/packages/lman/sdk)
[![PHP version](https://img.shields.io/packagist/dependency-v/lman/sdk/php)](https://packagist.org/packages/lman/sdk)
[![Packagist downloads](https://img.shields.io/packagist/dt/lman/sdk)](https://packagist.org/packages/lman/sdk)
[![License](https://img.shields.io/github/license/licenseman/licensemanager-php)](https://github.com/licenseman/licensemanager-php/blob/main/LICENSE)
[![Documentation](https://img.shields.io/badge/docs-licensemanager.dev-blue)](https://licensemanager.dev/docs/sdks/php)

The official PHP SDK for the [LicenseManager](https://licensemanager.dev) API: issue, manage and validate software licenses. Built on Guzzle, with a model class for each schema.

**[Documentation](https://licensemanager.dev/docs/sdks/php)** · **[API reference](https://api.licensemanager.dev/docs)** · **[Changelog](CHANGELOG.md)**

## Requirements

PHP 8.1 or later.

## Installation

```sh
composer require lman/sdk
```

## Usage

Create an API key in the LicenseManager app, then create a license after a sale:

```php
<?php

require __DIR__ . "/vendor/autoload.php";

use LicenseManager\Api\LicensesApi;
use LicenseManager\Configuration;
use LicenseManager\Model\CreateLicense;

$config = (new Configuration())
    ->setApiKey("x-api-key", getenv("LICENSEMANAGER_API_KEY"));
$licenses = new LicensesApi(config: $config);

$license = $licenses->createLicense("x7Kp2QaZ", new CreateLicense([
    "email" => "jane@example.com",
]));
```

And validate it from your application, which needs no API key:

```php
<?php

require __DIR__ . "/vendor/autoload.php";

use LicenseManager\Api\LicensesApi;
use LicenseManager\Model\ValidateKey;

$licenses = new LicensesApi();

$licenseToken = $licenses->validateKey("x7Kp2QaZ", new ValidateKey([
    "key" => "7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF",
    "fingerprint" => "4c:32:75:8f:9a:1e",
    "version" => "1.4.2",
]));
```

## Authentication

Most endpoints take an organization API key: keep it on your servers. The endpoints your application calls directly, like validating a key, take no credentials or a token scoped to a customer, license or machine. See [authentication](https://licensemanager.dev/docs/api/authentication) and [scoped tokens](https://licensemanager.dev/docs/api/scoped-tokens).

```php
use LicenseManager\Configuration;

// With an API key, from your backend:
$config = (new Configuration())->setApiKey("x-api-key", getenv("LICENSEMANAGER_API_KEY"));
// Or with a token scoped to a customer, license or machine:
$config = (new Configuration())->setAccessToken($token);
```

## Errors

Failed requests answer an error with a stable `code` to branch on, listed for each endpoint in the [API reference](https://api.licensemanager.dev/docs). See [errors](https://licensemanager.dev/docs/api/errors).

```php
use LicenseManager\ApiException;

try {
    $licenses->getLicense("l3Nv8KwB");
} catch (ApiException $error) {
    // The body is { "error": { "code", "message" } }.
    echo $error->getCode(), " ", $error->getResponseBody();
}
```

## Reference

Every method is documented, with its parameters and responses, in the [`docs`](docs) folder:

| Class | Methods |
| --- | --- |
| [`LicensesApi`](docs/Api/LicensesApi.md) | `validateKey`, `listLicenses`, `createLicense`, `listCustomerLicenses`, `getLicense`, `deleteLicense`, `updateLicense`, `getLicenseStats`, `cancelLicense`, `sendLicenseKeys`, `getSigningKey` |
| [`PortalApi`](docs/Api/PortalApi.md) | `getPortal`, `requestPortalLink`, `createPortalLink`, `sendPortalLink` |
| [`ProductsApi`](docs/Api/ProductsApi.md) | `listProducts`, `createProduct`, `getProduct`, `deleteProduct`, `updateProduct`, `resetProduct`, `uploadProductLogo`, `deleteProductLogo`, `getProductStats` |
| [`PoliciesApi`](docs/Api/PoliciesApi.md) | `listPolicies`, `createPolicy`, `getPolicy`, `deletePolicy`, `updatePolicy` |
| [`CustomersApi`](docs/Api/CustomersApi.md) | `listCustomers`, `createCustomer`, `getCustomer`, `deleteCustomer`, `updateCustomer` |
| [`MachinesApi`](docs/Api/MachinesApi.md) | `listMachines`, `getMachine`, `deactivateMachine` |
| [`ReleasesApi`](docs/Api/ReleasesApi.md) | `listReleases`, `createRelease`, `getRelease`, `deleteRelease`, `updateRelease` |
| [`TokensApi`](docs/Api/TokensApi.md) | `createCustomerToken`, `createLicenseToken`, `createMachineToken` |
| [`EventsApi`](docs/Api/EventsApi.md) | `listPolicyEvents`, `listLicenseEvents` |
| [`IntegrationsApi`](docs/Api/IntegrationsApi.md) | `getStripeIntegration`, `connectStripe`, `disconnectIntegration`, `updateIntegration`, `checkIntegration`, `listStripePrices`, `createStripeMapping`, `deleteStripeMapping`, `updateStripeMapping` |

## Versioning

This SDK follows [semantic versioning](https://semver.org) and is generated from the [OpenAPI document](openapi.json) of the API: each release is listed in the [changelog](CHANGELOG.md). Please don't open pull requests, they would be overwritten by the next release: [open an issue](https://github.com/licenseman/licensemanager-php/issues) instead.

## License

See [LICENSE](LICENSE).
