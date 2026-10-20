# LicenseManager\TokensApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createCustomerToken()**](TokensApi.md#createCustomerToken) | **POST** /v1/customers/{id}/tokens | Create a customer token |
| [**createLicenseToken()**](TokensApi.md#createLicenseToken) | **POST** /v1/licenses/{id}/tokens | Create a license token |
| [**createMachineToken()**](TokensApi.md#createMachineToken) | **POST** /v1/machines/{id}/tokens | Create a machine token |


## `createCustomerToken()`

```php
createCustomerToken($id, $create_token): \LicenseManager\Model\Token
```

Create a customer token

Creates a token scoped to the customer, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.  A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.  **Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\TokensApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = c9Wd3RtE; // string
$create_token = new \LicenseManager\Model\CreateToken(); // \LicenseManager\Model\CreateToken

try {
    $result = $apiInstance->createCustomerToken($id, $create_token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TokensApi->createCustomerToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **create_token** | [**\LicenseManager\Model\CreateToken**](../Model/CreateToken.md)|  | |

### Return type

[**\LicenseManager\Model\Token**](../Model/Token.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createLicenseToken()`

```php
createLicenseToken($id, $create_token): \LicenseManager\Model\Token
```

Create a license token

Creates a token scoped to the license, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.  A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.  **Token access**: customer tokens. A customer token creates tokens for its customer's licenses, with the permissions and at most the expiration it has.  **Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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


$apiInstance = new LicenseManager\Api\TokensApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = c9Wd3RtE; // string
$create_token = new \LicenseManager\Model\CreateToken(); // \LicenseManager\Model\CreateToken

try {
    $result = $apiInstance->createLicenseToken($id, $create_token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TokensApi->createLicenseToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **create_token** | [**\LicenseManager\Model\CreateToken**](../Model/CreateToken.md)|  | |

### Return type

[**\LicenseManager\Model\Token**](../Model/Token.md)

### Authorization

[apiKey](../../README.md#apiKey), [token](../../README.md#token)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createMachineToken()`

```php
createMachineToken($id, $create_token): \LicenseManager\Model\Token
```

Create a machine token

Creates a token scoped to the machine, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.  A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.  **Token access**: customer, license tokens. A customer or license token creates tokens for the machines it reaches, with the permissions and at most the expiration it has.  **Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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


$apiInstance = new LicenseManager\Api\TokensApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = c9Wd3RtE; // string
$create_token = new \LicenseManager\Model\CreateToken(); // \LicenseManager\Model\CreateToken

try {
    $result = $apiInstance->createMachineToken($id, $create_token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TokensApi->createMachineToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **create_token** | [**\LicenseManager\Model\CreateToken**](../Model/CreateToken.md)|  | |

### Return type

[**\LicenseManager\Model\Token**](../Model/Token.md)

### Authorization

[apiKey](../../README.md#apiKey), [token](../../README.md#token)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
