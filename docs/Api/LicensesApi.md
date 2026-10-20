# LicenseManager\LicensesApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createLicense()**](LicensesApi.md#createLicense) | **POST** /v1/products/{productId}/licenses | Create a license |
| [**deleteLicense()**](LicensesApi.md#deleteLicense) | **DELETE** /v1/licenses/{id} | Delete a license |
| [**getLicense()**](LicensesApi.md#getLicense) | **GET** /v1/licenses/{id} | Get a license |
| [**getLicenseStats()**](LicensesApi.md#getLicenseStats) | **GET** /v1/licenses/{id}/stats | Get the stats of a license |
| [**getSigningKey()**](LicensesApi.md#getSigningKey) | **GET** /v1/signing-key | Get the organization&#39;s signing key |
| [**listCustomerLicenses()**](LicensesApi.md#listCustomerLicenses) | **GET** /v1/customers/{customerId}/licenses | List the licenses of a customer |
| [**listLicenses()**](LicensesApi.md#listLicenses) | **GET** /v1/products/{productId}/licenses | List the licenses of a product |
| [**sendLicenseKeys()**](LicensesApi.md#sendLicenseKeys) | **POST** /v1/licenses/send-keys | Email license keys to their customers |
| [**updateLicense()**](LicensesApi.md#updateLicense) | **PATCH** /v1/licenses/{id} | Update a license |
| [**validateKey()**](LicensesApi.md#validateKey) | **POST** /v1/products/{productId}/validate-key | Validate a license key |


## `createLicense()`

```php
createLicense($product_id, $create_license): \LicenseManager\Model\License
```

Create a license

Without a `key`, the license gets a random one, like `7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF`: 5 groups of 5 characters separated by dashes, each character an upper case letter or a digit other than `O`, `0`, `I` and `1`. That's 32 possible characters encoding 5 bits each, for 125 random bits.  Without a `policyId`, the license follows the product's default policy.  Without an `expiresAt`, the license expires after the duration of its policy, or never when the policy has none. `expiresAt: null` makes it never expire.  Without a `price`, the price paid for the license is unknown: it's left out of the revenue stats.  The values of `maxVersion` left out are taken from the max version of the policy: its hard-coded version, or the times after the creation of the license its versions lock.  The license belongs to the product's customer with the given `email`, which is created when there's none.  With `sendKey: true`, the key is emailed to the customer once the license is created.  The license copies the settings of its policy when it's created: later changes to the policy don't affect it. Its key, policy and customer can't be changed afterwards.  **Required role permission**: `license:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string
$create_license = new \LicenseManager\Model\CreateLicense(); // \LicenseManager\Model\CreateLicense

try {
    $result = $apiInstance->createLicense($product_id, $create_license);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->createLicense: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **create_license** | [**\LicenseManager\Model\CreateLicense**](../Model/CreateLicense.md)|  | |

### Return type

[**\LicenseManager\Model\License**](../Model/License.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteLicense()`

```php
deleteLicense($id)
```

Delete a license

Deletes the license along with its deactivated machines. A license used on active machines can't be deleted: deactivate them first. The tokens scoped to the license or its machines stop working, but the license tokens `validateKey` already returned stay valid until they expire. Its events can no longer be listed.  **Required role permission**: `license:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = l3Nv8KwB; // string

try {
    $apiInstance->deleteLicense($id);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->deleteLicense: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getLicense()`

```php
getLicense($id): \LicenseManager\Model\License
```

Get a license

**Token access**: customer, license, machine tokens with the `license:read` permission (or the matching write one). A token reaches the license it's scoped to, the licenses of its customer, or the license of its machine.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');

// Configure Bearer (JWT) authorization: token
$config = LicenseManager\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = l3Nv8KwB; // string

try {
    $result = $apiInstance->getLicense($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->getLicense: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\License**](../Model/License.md)

### Authorization

[apiKey](../../README.md#apiKey), [token](../../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getLicenseStats()`

```php
getLicenseStats($id): \LicenseManager\Model\LicenseStats
```

Get the stats of a license

Daily number of successful activations of the license over the last 90 days, today included, per machine and per version of the application. Days are in UTC.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = l3Nv8KwB; // string

try {
    $result = $apiInstance->getLicenseStats($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->getLicenseStats: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\LicenseStats**](../Model/LicenseStats.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getSigningKey()`

```php
getSigningKey(): \LicenseManager\Model\SigningKey
```

Get the organization's signing key

Public key verifying the license tokens returned by `validateKey`, to embed in applications. Created the first time it's needed, and never rotated. The organization has a single key, signing the tokens of its live and test products alike: check the tokens' `aud` to tell them apart.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getSigningKey();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->getSigningKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\LicenseManager\Model\SigningKey**](../Model/SigningKey.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listCustomerLicenses()`

```php
listCustomerLicenses($customer_id, $page, $page_size, $sort, $search, $key, $policy_id, $machine_version, $status, $created_from, $created_to, $last_activated_from, $last_activated_to, $never_activated, $expires_from, $expires_to, $never_expires, $currency, $price, $price_min, $price_max, $has_price): \LicenseManager\Model\LicenseList
```

List the licenses of a customer

Sorting by `lastActivatedAt` puts the licenses never activated last in both orders. Sorting by `price` compares the amounts whatever their currency, and puts the licenses without a price last in both orders.  **Token access**: customer tokens with the `license:read` permission (or the matching write one). A customer token reaches its own licenses.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');

// Configure Bearer (JWT) authorization: token
$config = LicenseManager\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$customer_id = c9Wd3RtE; // string
$page = 1; // int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
$page_size = 20; // int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
$sort = -createdAt; // string | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
$search = X9ZPA; // string | Case-insensitive text the key contains.
$key = 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF; // string | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`.
$policy_id = p4Rt8LmQ; // string | Only returns the licenses following this policy.
$machine_version = 2.3.1; // string | Only returns the licenses with at least one active machine running this version of the product.
$status = new \LicenseManager\Model\\LicenseManagerModelLicenseStatus(); // \LicenseManagerModelLicenseStatus | Only returns the licenses with this status.
$created_from = 2026-01-01T00:00:00.000Z; // \DateTime | Only returns the licenses created at or after this date.
$created_to = 2026-02-01T00:00:00.000Z; // \DateTime | Only returns the licenses created at or before this date.
$last_activated_from = 2026-01-01T00:00:00.000Z; // \DateTime | Only returns the licenses last activated at or after this date. Licenses never activated are left out.
$last_activated_to = 2026-02-01T00:00:00.000Z; // \DateTime | Only returns the licenses last activated at or before this date. Licenses never activated are left out.
$never_activated = true; // string | `true` only returns the licenses never activated, `false` only the ones activated at least once.
$expires_from = 2026-01-01T00:00:00.000Z; // \DateTime | Only returns the licenses expiring at or after this date. Licenses that never expire are left out.
$expires_to = 2026-02-01T00:00:00.000Z; // \DateTime | Only returns the licenses expiring at or before this date. Licenses that never expire are left out.
$never_expires = true; // string | `true` only returns the licenses that never expire, `false` only the ones with an expiration date.
$currency = USD; // string | Only returns the licenses paid in this currency.
$price = 49.99; // float | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
$price_min = 49.99; // float | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
$price_max = 49.99; // float | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
$has_price = true; // string | `true` only returns the licenses with a price, `false` only the ones without.

try {
    $result = $apiInstance->listCustomerLicenses($customer_id, $page, $page_size, $sort, $search, $key, $policy_id, $machine_version, $status, $created_from, $created_to, $last_activated_from, $last_activated_to, $never_activated, $expires_from, $expires_to, $never_expires, $currency, $price, $price_min, $price_max, $has_price);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->listCustomerLicenses: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **customer_id** | **string**|  | |
| **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **string**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;] |
| **search** | **string**| Case-insensitive text the key contains. | [optional] |
| **key** | **string**| Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [optional] |
| **policy_id** | **string**| Only returns the licenses following this policy. | [optional] |
| **machine_version** | **string**| Only returns the licenses with at least one active machine running this version of the product. | [optional] |
| **status** | [**\LicenseManagerModelLicenseStatus**](../Model/.md)| Only returns the licenses with this status. | [optional] |
| **created_from** | **\DateTime**| Only returns the licenses created at or after this date. | [optional] |
| **created_to** | **\DateTime**| Only returns the licenses created at or before this date. | [optional] |
| **last_activated_from** | **\DateTime**| Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [optional] |
| **last_activated_to** | **\DateTime**| Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [optional] |
| **never_activated** | **string**| &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [optional] |
| **expires_from** | **\DateTime**| Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [optional] |
| **expires_to** | **\DateTime**| Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [optional] |
| **never_expires** | **string**| &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [optional] |
| **currency** | **string**| Only returns the licenses paid in this currency. | [optional] |
| **price** | **float**| Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **price_min** | **float**| Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **price_max** | **float**| Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **has_price** | **string**| &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [optional] |

### Return type

[**\LicenseManager\Model\LicenseList**](../Model/LicenseList.md)

### Authorization

[apiKey](../../README.md#apiKey), [token](../../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listLicenses()`

```php
listLicenses($product_id, $page, $page_size, $sort, $search, $key, $policy_id, $customer_id, $machine_version, $status, $created_from, $created_to, $last_activated_from, $last_activated_to, $never_activated, $expires_from, $expires_to, $never_expires, $currency, $price, $price_min, $price_max, $has_price): \LicenseManager\Model\LicenseList
```

List the licenses of a product

Sorting by `lastActivatedAt` puts the licenses never activated last in both orders. Sorting by `price` compares the amounts whatever their currency, and puts the licenses without a price last in both orders.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string
$page = 1; // int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
$page_size = 20; // int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
$sort = -createdAt; // string | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
$search = X9ZPA; // string | Case-insensitive text the key contains.
$key = 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF; // string | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`.
$policy_id = p4Rt8LmQ; // string | Only returns the licenses following this policy.
$customer_id = c9Wd3RtE; // string | Only returns the licenses of this customer.
$machine_version = 2.3.1; // string | Only returns the licenses with at least one active machine running this version of the product.
$status = new \LicenseManager\Model\\LicenseManagerModelLicenseStatus(); // \LicenseManagerModelLicenseStatus | Only returns the licenses with this status.
$created_from = 2026-01-01T00:00:00.000Z; // \DateTime | Only returns the licenses created at or after this date.
$created_to = 2026-02-01T00:00:00.000Z; // \DateTime | Only returns the licenses created at or before this date.
$last_activated_from = 2026-01-01T00:00:00.000Z; // \DateTime | Only returns the licenses last activated at or after this date. Licenses never activated are left out.
$last_activated_to = 2026-02-01T00:00:00.000Z; // \DateTime | Only returns the licenses last activated at or before this date. Licenses never activated are left out.
$never_activated = true; // string | `true` only returns the licenses never activated, `false` only the ones activated at least once.
$expires_from = 2026-01-01T00:00:00.000Z; // \DateTime | Only returns the licenses expiring at or after this date. Licenses that never expire are left out.
$expires_to = 2026-02-01T00:00:00.000Z; // \DateTime | Only returns the licenses expiring at or before this date. Licenses that never expire are left out.
$never_expires = true; // string | `true` only returns the licenses that never expire, `false` only the ones with an expiration date.
$currency = USD; // string | Only returns the licenses paid in this currency.
$price = 49.99; // float | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
$price_min = 49.99; // float | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
$price_max = 49.99; // float | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
$has_price = true; // string | `true` only returns the licenses with a price, `false` only the ones without.

try {
    $result = $apiInstance->listLicenses($product_id, $page, $page_size, $sort, $search, $key, $policy_id, $customer_id, $machine_version, $status, $created_from, $created_to, $last_activated_from, $last_activated_to, $never_activated, $expires_from, $expires_to, $never_expires, $currency, $price, $price_min, $price_max, $has_price);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->listLicenses: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **string**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;] |
| **search** | **string**| Case-insensitive text the key contains. | [optional] |
| **key** | **string**| Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [optional] |
| **policy_id** | **string**| Only returns the licenses following this policy. | [optional] |
| **customer_id** | **string**| Only returns the licenses of this customer. | [optional] |
| **machine_version** | **string**| Only returns the licenses with at least one active machine running this version of the product. | [optional] |
| **status** | [**\LicenseManagerModelLicenseStatus**](../Model/.md)| Only returns the licenses with this status. | [optional] |
| **created_from** | **\DateTime**| Only returns the licenses created at or after this date. | [optional] |
| **created_to** | **\DateTime**| Only returns the licenses created at or before this date. | [optional] |
| **last_activated_from** | **\DateTime**| Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [optional] |
| **last_activated_to** | **\DateTime**| Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [optional] |
| **never_activated** | **string**| &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [optional] |
| **expires_from** | **\DateTime**| Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [optional] |
| **expires_to** | **\DateTime**| Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [optional] |
| **never_expires** | **string**| &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [optional] |
| **currency** | **string**| Only returns the licenses paid in this currency. | [optional] |
| **price** | **float**| Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **price_min** | **float**| Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **price_max** | **float**| Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **has_price** | **string**| &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [optional] |

### Return type

[**\LicenseManager\Model\LicenseList**](../Model/LicenseList.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendLicenseKeys()`

```php
sendLicenseKeys($send_license_keys)
```

Email license keys to their customers

Emails each customer the keys of its licenses among `ids`, with their expiration date: one email per customer, whatever their number of licenses. The licenses can belong to different products of the organization.  Test products only email the members of the organization, so testing never emails real customers: nothing is sent when a license of a test product belongs to a customer whose email isn't a member's.  **Required role permission**: `license:send` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$send_license_keys = new \LicenseManager\Model\SendLicenseKeys(); // \LicenseManager\Model\SendLicenseKeys

try {
    $apiInstance->sendLicenseKeys($send_license_keys);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->sendLicenseKeys: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **send_license_keys** | [**\LicenseManager\Model\SendLicenseKeys**](../Model/SendLicenseKeys.md)|  | |

### Return type

void (empty response body)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateLicense()`

```php
updateLicense($id, $update_license): \LicenseManager\Model\License
```

Update a license

The key, policy and customer of a license can't be changed: sending them does nothing.  The changes apply to the next validations of the key, not to the license tokens `validateKey` already returned, which stay valid until they expire. Lowering `maxMachines` doesn't deactivate machines: the ones already active keep validating, and new ones are refused until enough are deactivated.  **Required role permission**: `license:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = l3Nv8KwB; // string
$update_license = new \LicenseManager\Model\UpdateLicense(); // \LicenseManager\Model\UpdateLicense

try {
    $result = $apiInstance->updateLicense($id, $update_license);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->updateLicense: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_license** | [**\LicenseManager\Model\UpdateLicense**](../Model/UpdateLicense.md)|  | |

### Return type

[**\LicenseManager\Model\License**](../Model/License.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `validateKey()`

```php
validateKey($product_id, $validate_key): \LicenseManager\Model\LicenseToken
```

Validate a license key

Checks the license key of the product on a machine and returns a token the application can verify offline with the organization's public key. Doesn't need authentication.  The license must allow the `version`: up to its `maxVersion.version` when it has one, like `\"2.3\"` for every 2.3.z version and older. Its `maxVersion.lockMajorAt` and `maxVersion.lockMinorAt` are enforced once they hard-code `maxVersion.version`, within the hour they're reached. When it doesn't, the error's `latestAllowedVersion` is the latest release of the product the license allows, so the application can offer to install it.  The machine with the `fingerprint` is created when the license has none, and activated when it's deactivated, unless the license is already active on its maximum number of machines. A machine that's already active is never refused for the maximum number of machines, even when it was lowered below the number of active machines. Its `version`, and its `name` and `platform` when given, are updated: they can't be cleared.  The checks run in this order, and the first one failing answers: the license has expired, then it doesn't allow the version, then it's on its maximum number of machines. Each failure is recorded as a `license.validation_failed` event, except for keys that don't exist.  Changes to the license, like deactivating the machine or shortening its expiration, don't revoke the tokens already returned: the application only sees them when it validates its key again, at the latest when its token expires.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new LicenseManager\Api\LicensesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$product_id = x7Kp2QaZ; // string
$validate_key = new \LicenseManager\Model\ValidateKey(); // \LicenseManager\Model\ValidateKey

try {
    $result = $apiInstance->validateKey($product_id, $validate_key);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LicensesApi->validateKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **validate_key** | [**\LicenseManager\Model\ValidateKey**](../Model/ValidateKey.md)|  | |

### Return type

[**\LicenseManager\Model\LicenseToken**](../Model/LicenseToken.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
