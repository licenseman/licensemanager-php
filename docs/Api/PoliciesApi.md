# LicenseManager\PoliciesApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createPolicy()**](PoliciesApi.md#createPolicy) | **POST** /v1/products/{productId}/policies | Create a policy |
| [**deletePolicy()**](PoliciesApi.md#deletePolicy) | **DELETE** /v1/policies/{id} | Delete a policy |
| [**getPolicy()**](PoliciesApi.md#getPolicy) | **GET** /v1/policies/{id} | Get a policy |
| [**listPolicies()**](PoliciesApi.md#listPolicies) | **GET** /v1/products/{productId}/policies | List the policies of a product |
| [**updatePolicy()**](PoliciesApi.md#updatePolicy) | **PATCH** /v1/policies/{id} | Update a policy |


## `createPolicy()`

```php
createPolicy($product_id, $create_policy): \LicenseManager\Model\Policy
```

Create a policy

Without a `slug`, the policy gets one derived from its name, made unique within the product by appending a dash and 3 random lowercase letters or digits when needed. An explicit `slug` is used as is: the request fails with a `409` when it's taken.  With `isDefault: true`, the new policy replaces the product's current default policy.  A product always has a default policy, so when it has no policies the new one becomes the default: the request fails with a `409` when `isDefault` is `false`.  **Required role permission**: `policy:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\PoliciesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string
$create_policy = new \LicenseManager\Model\CreatePolicy(); // \LicenseManager\Model\CreatePolicy

try {
    $result = $apiInstance->createPolicy($product_id, $create_policy);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PoliciesApi->createPolicy: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **create_policy** | [**\LicenseManager\Model\CreatePolicy**](../Model/CreatePolicy.md)|  | |

### Return type

[**\LicenseManager\Model\Policy**](../Model/Policy.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deletePolicy()`

```php
deletePolicy($id)
```

Delete a policy

Deleting the default policy makes the oldest remaining policy of the product the default. The last policy of a product can't be deleted, nor a policy that licenses follow. Its events can no longer be listed.  **Required role permission**: `policy:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\PoliciesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = p4Rt8LmQ; // string

try {
    $apiInstance->deletePolicy($id);
} catch (Exception $e) {
    echo 'Exception when calling PoliciesApi->deletePolicy: ', $e->getMessage(), PHP_EOL;
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

## `getPolicy()`

```php
getPolicy($id): \LicenseManager\Model\Policy
```

Get a policy

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\PoliciesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = p4Rt8LmQ; // string

try {
    $result = $apiInstance->getPolicy($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PoliciesApi->getPolicy: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\Policy**](../Model/Policy.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listPolicies()`

```php
listPolicies($product_id, $page, $page_size, $sort, $search, $slug, $is_default, $license_count, $license_count_min, $license_count_max): \LicenseManager\Model\PolicyList
```

List the policies of a product

`?isDefault=true` returns the product's default policy alone: a product always has exactly one. Sorting by `duration` counts months for their average length, about 30.4 days.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\PoliciesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string
$page = 1; // int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
$page_size = 20; // int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
$sort = name; // string | Field to sort by, prefixed with `-` for descending order. Defaults to `name`.
$search = pro; // string | Case-insensitive text the name or slug contains.
$slug = yearly; // string | Only returns the policy with this exact slug.
$is_default = true; // string | `true` only returns the product's default policy, `false` only the other ones.
$license_count = 1; // int | Only returns the policies followed by exactly this number of licenses.
$license_count_min = 1; // int | Only returns the policies followed by at least this number of licenses.
$license_count_max = 1; // int | Only returns the policies followed by at most this number of licenses.

try {
    $result = $apiInstance->listPolicies($product_id, $page, $page_size, $sort, $search, $slug, $is_default, $license_count, $license_count_min, $license_count_max);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PoliciesApi->listPolicies: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **string**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;name&#x60;. | [optional] [default to &#39;name&#39;] |
| **search** | **string**| Case-insensitive text the name or slug contains. | [optional] |
| **slug** | **string**| Only returns the policy with this exact slug. | [optional] |
| **is_default** | **string**| &#x60;true&#x60; only returns the product&#39;s default policy, &#x60;false&#x60; only the other ones. | [optional] |
| **license_count** | **int**| Only returns the policies followed by exactly this number of licenses. | [optional] |
| **license_count_min** | **int**| Only returns the policies followed by at least this number of licenses. | [optional] |
| **license_count_max** | **int**| Only returns the policies followed by at most this number of licenses. | [optional] |

### Return type

[**\LicenseManager\Model\PolicyList**](../Model/PolicyList.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updatePolicy()`

```php
updatePolicy($id, $update_policy): \LicenseManager\Model\Policy
```

Update a policy

`isDefault: true` makes the policy the product's default, in place of the current one. A product always has a default policy, so the default can't be unset with `isDefault: false`: make another policy the default instead.  Licenses copy the settings of their policy when they're created, so changing them only affects the licenses created afterwards: update the existing licenses to change theirs.  **Required role permission**: `policy:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\PoliciesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = p4Rt8LmQ; // string
$update_policy = new \LicenseManager\Model\UpdatePolicy(); // \LicenseManager\Model\UpdatePolicy

try {
    $result = $apiInstance->updatePolicy($id, $update_policy);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PoliciesApi->updatePolicy: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_policy** | [**\LicenseManager\Model\UpdatePolicy**](../Model/UpdatePolicy.md)|  | |

### Return type

[**\LicenseManager\Model\Policy**](../Model/Policy.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
