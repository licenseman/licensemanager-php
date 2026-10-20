# LicenseManager\ReleasesApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createRelease()**](ReleasesApi.md#createRelease) | **POST** /v1/products/{productId}/releases | Create a release |
| [**deleteRelease()**](ReleasesApi.md#deleteRelease) | **DELETE** /v1/releases/{id} | Delete a release |
| [**getRelease()**](ReleasesApi.md#getRelease) | **GET** /v1/releases/{id} | Get a release |
| [**listReleases()**](ReleasesApi.md#listReleases) | **GET** /v1/products/{productId}/releases | List the releases of a product |
| [**updateRelease()**](ReleasesApi.md#updateRelease) | **PATCH** /v1/releases/{id} | Update a release |


## `createRelease()`

```php
createRelease($product_id, $create_release): \LicenseManager\Model\Release
```

Create a release

Releases don't restrict which versions `validateKey` accepts: a machine can run a version without a release. They give the `latestAllowedVersion` of its `version_not_allowed` errors, among the stable releases already released, and the number of active machines running each version.  **Required role permission**: `release:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ReleasesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string
$create_release = new \LicenseManager\Model\CreateRelease(); // \LicenseManager\Model\CreateRelease

try {
    $result = $apiInstance->createRelease($product_id, $create_release);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ReleasesApi->createRelease: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **create_release** | [**\LicenseManager\Model\CreateRelease**](../Model/CreateRelease.md)|  | |

### Return type

[**\LicenseManager\Model\Release**](../Model/Release.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteRelease()`

```php
deleteRelease($id)
```

Delete a release

**Required role permission**: `release:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ReleasesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = r4Lm8VwX; // string

try {
    $apiInstance->deleteRelease($id);
} catch (Exception $e) {
    echo 'Exception when calling ReleasesApi->deleteRelease: ', $e->getMessage(), PHP_EOL;
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

## `getRelease()`

```php
getRelease($id): \LicenseManager\Model\Release
```

Get a release

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ReleasesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = r4Lm8VwX; // string

try {
    $result = $apiInstance->getRelease($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ReleasesApi->getRelease: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\Release**](../Model/Release.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listReleases()`

```php
listReleases($product_id, $page, $page_size, $sort, $search, $released_from, $released_to, $active_machine_count, $active_machine_count_min, $active_machine_count_max): \LicenseManager\Model\ReleaseList
```

List the releases of a product

Sorting by `version` compares the major, minor and patch numbers as numbers, then puts a pre-release before its stable release. Pre-releases of the same version compare as text, unlike semantic versioning: `2.0.0-beta.10` comes before `2.0.0-beta.2`. Build metadata is ignored.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ReleasesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string
$page = 1; // int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
$page_size = 20; // int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
$sort = -version; // string | Field to sort by, prefixed with `-` for descending order. Defaults to `-version`.
$search = 2.3; // string | Case-insensitive text the version contains.
$released_from = 2026-01-01T00:00:00.000Z; // \DateTime | Only returns the releases released at or after this date.
$released_to = 2026-02-01T00:00:00.000Z; // \DateTime | Only returns the releases released at or before this date.
$active_machine_count = 1; // int | Only returns the releases running on exactly this number of active machines.
$active_machine_count_min = 1; // int | Only returns the releases running on at least this number of active machines.
$active_machine_count_max = 1; // int | Only returns the releases running on at most this number of active machines.

try {
    $result = $apiInstance->listReleases($product_id, $page, $page_size, $sort, $search, $released_from, $released_to, $active_machine_count, $active_machine_count_min, $active_machine_count_max);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ReleasesApi->listReleases: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **string**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-version&#x60;. | [optional] [default to &#39;-version&#39;] |
| **search** | **string**| Case-insensitive text the version contains. | [optional] |
| **released_from** | **\DateTime**| Only returns the releases released at or after this date. | [optional] |
| **released_to** | **\DateTime**| Only returns the releases released at or before this date. | [optional] |
| **active_machine_count** | **int**| Only returns the releases running on exactly this number of active machines. | [optional] |
| **active_machine_count_min** | **int**| Only returns the releases running on at least this number of active machines. | [optional] |
| **active_machine_count_max** | **int**| Only returns the releases running on at most this number of active machines. | [optional] |

### Return type

[**\LicenseManager\Model\ReleaseList**](../Model/ReleaseList.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateRelease()`

```php
updateRelease($id, $update_release): \LicenseManager\Model\Release
```

Update a release

**Required role permission**: `release:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ReleasesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = r4Lm8VwX; // string
$update_release = new \LicenseManager\Model\UpdateRelease(); // \LicenseManager\Model\UpdateRelease

try {
    $result = $apiInstance->updateRelease($id, $update_release);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ReleasesApi->updateRelease: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_release** | [**\LicenseManager\Model\UpdateRelease**](../Model/UpdateRelease.md)|  | |

### Return type

[**\LicenseManager\Model\Release**](../Model/Release.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
