# LicenseManager\MachinesApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**deactivateMachine()**](MachinesApi.md#deactivateMachine) | **POST** /v1/machines/{id}/deactivate | Deactivate a machine |
| [**getMachine()**](MachinesApi.md#getMachine) | **GET** /v1/machines/{id} | Get a machine |
| [**listMachines()**](MachinesApi.md#listMachines) | **GET** /v1/licenses/{licenseId}/machines | List the machines of a license |


## `deactivateMachine()`

```php
deactivateMachine($id): \LicenseManager\Model\Machine
```

Deactivate a machine

The machine no longer counts as using the license, freeing its place when the license has a maximum number of machines. Validating the license key on the machine activates it again, unless the license is on its maximum number of machines by then. Deactivating a deactivated machine does nothing.  The license token `validateKey` returned to the machine isn't revoked: the application can keep running offline until it expires. Machines can't be deleted: they're deleted with their license.  **Token access**: customer, license, machine tokens with the `machine:write` permission (or the matching write one). A token reaches the machine it's scoped to, or the machines of its license or customer.  **Required role permission**: `machine:deactivate` when called with a session, granted by the member's role. API keys aren't limited by roles.

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


$apiInstance = new LicenseManager\Api\MachinesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = m9Tq3VhD; // string

try {
    $result = $apiInstance->deactivateMachine($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MachinesApi->deactivateMachine: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\Machine**](../Model/Machine.md)

### Authorization

[apiKey](../../README.md#apiKey), [token](../../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMachine()`

```php
getMachine($id): \LicenseManager\Model\Machine
```

Get a machine

**Token access**: customer, license, machine tokens with the `machine:read` permission (or the matching write one). A token reaches the machine it's scoped to, or the machines of its license or customer.

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


$apiInstance = new LicenseManager\Api\MachinesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = m9Tq3VhD; // string

try {
    $result = $apiInstance->getMachine($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MachinesApi->getMachine: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\Machine**](../Model/Machine.md)

### Authorization

[apiKey](../../README.md#apiKey), [token](../../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listMachines()`

```php
listMachines($license_id, $page, $page_size, $sort, $search, $fingerprint, $status): \LicenseManager\Model\MachineList
```

List the machines of a license

**Token access**: customer, license tokens with the `machine:read` permission (or the matching write one). A token reaches the license it's scoped to, or the licenses of its customer.

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


$apiInstance = new LicenseManager\Api\MachinesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$license_id = l3Nv8KwB; // string
$page = 1; // int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
$page_size = 20; // int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
$sort = -createdAt; // string | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
$search = macbook; // string | Case-insensitive text the fingerprint or name contains.
$fingerprint = 4c:32:75:8f:9a:1e; // string | Only returns the machine with this exact fingerprint.
$status = active; // string | Only returns the machines with this status.

try {
    $result = $apiInstance->listMachines($license_id, $page, $page_size, $sort, $search, $fingerprint, $status);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MachinesApi->listMachines: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **license_id** | **string**|  | |
| **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **string**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;] |
| **search** | **string**| Case-insensitive text the fingerprint or name contains. | [optional] |
| **fingerprint** | **string**| Only returns the machine with this exact fingerprint. | [optional] |
| **status** | **string**| Only returns the machines with this status. | [optional] |

### Return type

[**\LicenseManager\Model\MachineList**](../Model/MachineList.md)

### Authorization

[apiKey](../../README.md#apiKey), [token](../../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
