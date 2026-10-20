# LicenseManager\EventsApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**listLicenseEvents()**](EventsApi.md#listLicenseEvents) | **GET** /v1/licenses/{id}/events | List the events of a license |
| [**listPolicyEvents()**](EventsApi.md#listPolicyEvents) | **GET** /v1/policies/{id}/events | List the events of a policy |


## `listLicenseEvents()`

```php
listLicenseEvents($id, $page, $page_size, $sort, $type, $machine_id): \LicenseManager\Model\EventList
```

List the events of a license

Includes the validations of the license on each of its machines. Doesn't accept tokens: only API keys and sessions.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\EventsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = l3Nv8KwB; // string
$page = 1; // int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
$page_size = 20; // int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
$sort = -createdAt; // string | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
$type = new \LicenseManager\Model\\LicenseManager\Model\ListPolicyEventsTypeParameter(); // \LicenseManager\Model\ListPolicyEventsTypeParameter | Only returns the events of this type. Repeat it to return the events of any of these types.
$machine_id = m9Tq3VhD; // string | Only returns the events of this machine of the license.

try {
    $result = $apiInstance->listLicenseEvents($id, $page, $page_size, $sort, $type, $machine_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EventsApi->listLicenseEvents: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **string**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;] |
| **type** | [**\LicenseManager\Model\ListPolicyEventsTypeParameter**](../Model/.md)| Only returns the events of this type. Repeat it to return the events of any of these types. | [optional] |
| **machine_id** | **string**| Only returns the events of this machine of the license. | [optional] |

### Return type

[**\LicenseManager\Model\EventList**](../Model/EventList.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listPolicyEvents()`

```php
listPolicyEvents($id, $page, $page_size, $sort, $type): \LicenseManager\Model\EventList
```

List the events of a policy

Doesn't accept tokens: only API keys and sessions.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\EventsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = l3Nv8KwB; // string
$page = 1; // int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
$page_size = 20; // int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
$sort = -createdAt; // string | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
$type = new \LicenseManager\Model\\LicenseManager\Model\ListPolicyEventsTypeParameter(); // \LicenseManager\Model\ListPolicyEventsTypeParameter | Only returns the events of this type. Repeat it to return the events of any of these types.

try {
    $result = $apiInstance->listPolicyEvents($id, $page, $page_size, $sort, $type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EventsApi->listPolicyEvents: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **string**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;] |
| **type** | [**\LicenseManager\Model\ListPolicyEventsTypeParameter**](../Model/.md)| Only returns the events of this type. Repeat it to return the events of any of these types. | [optional] |

### Return type

[**\LicenseManager\Model\EventList**](../Model/EventList.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
