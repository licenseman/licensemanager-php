# LicenseManager\IntegrationsApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**checkIntegration()**](IntegrationsApi.md#checkIntegration) | **POST** /v1/integrations/{id}/check | Check an integration |
| [**connectStripe()**](IntegrationsApi.md#connectStripe) | **PUT** /v1/products/{productId}/integrations/stripe | Connect Stripe |
| [**createStripeMapping()**](IntegrationsApi.md#createStripeMapping) | **POST** /v1/products/{productId}/integrations/stripe/mappings | Map a Stripe price to a policy |
| [**deleteStripeMapping()**](IntegrationsApi.md#deleteStripeMapping) | **DELETE** /v1/integration-mappings/{id} | Delete a mapping |
| [**disconnectIntegration()**](IntegrationsApi.md#disconnectIntegration) | **DELETE** /v1/integrations/{id} | Disconnect an integration |
| [**getStripeIntegration()**](IntegrationsApi.md#getStripeIntegration) | **GET** /v1/products/{productId}/integrations/stripe | Get the Stripe integration of a product |
| [**listStripePrices()**](IntegrationsApi.md#listStripePrices) | **GET** /v1/integrations/{id}/stripe/prices | List the Stripe prices of an integration |
| [**updateIntegration()**](IntegrationsApi.md#updateIntegration) | **PATCH** /v1/integrations/{id} | Update an integration |
| [**updateStripeMapping()**](IntegrationsApi.md#updateStripeMapping) | **PATCH** /v1/integration-mappings/{id} | Change the policy of a mapping |


## `checkIntegration()`

```php
checkIntegration($id): \LicenseManager\Model\Integration
```

Check an integration

Checks right away, as done every day, that the API key still works and can manage the webhook endpoint, which is pointed at the server's webhook URL again (or created again when it was deleted). Updates the status. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = i8Fz4QnRt; // string

try {
    $result = $apiInstance->checkIntegration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->checkIntegration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\Integration**](../Model/Integration.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `connectStripe()`

```php
connectStripe($product_id, $connect_stripe): \LicenseManager\Model\StripeIntegration
```

Connect Stripe

Connects the Stripe account of the API key for the organization's products of the product's mode, or replaces the key of the existing connection. Checks the key works and has the required permissions, then creates a webhook endpoint on the account, telling the app about payments. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string
$connect_stripe = new \LicenseManager\Model\ConnectStripe(); // \LicenseManager\Model\ConnectStripe

try {
    $result = $apiInstance->connectStripe($product_id, $connect_stripe);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->connectStripe: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **connect_stripe** | [**\LicenseManager\Model\ConnectStripe**](../Model/ConnectStripe.md)|  | |

### Return type

[**\LicenseManager\Model\StripeIntegration**](../Model/StripeIntegration.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createStripeMapping()`

```php
createStripeMapping($product_id, $create_integration_mapping): \LicenseManager\Model\IntegrationMapping
```

Map a Stripe price to a policy

Paying the price then creates licenses of the product with the policy: one per unit bought. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string
$create_integration_mapping = new \LicenseManager\Model\CreateIntegrationMapping(); // \LicenseManager\Model\CreateIntegrationMapping

try {
    $result = $apiInstance->createStripeMapping($product_id, $create_integration_mapping);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->createStripeMapping: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **create_integration_mapping** | [**\LicenseManager\Model\CreateIntegrationMapping**](../Model/CreateIntegrationMapping.md)|  | |

### Return type

[**\LicenseManager\Model\IntegrationMapping**](../Model/IntegrationMapping.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteStripeMapping()`

```php
deleteStripeMapping($id)
```

Delete a mapping

Paying the price no longer creates licenses. The licenses it created stay. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = i8Fz4QnRt; // string

try {
    $apiInstance->deleteStripeMapping($id);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->deleteStripeMapping: ', $e->getMessage(), PHP_EOL;
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

## `disconnectIntegration()`

```php
disconnectIntegration($id)
```

Disconnect an integration

Deletes the webhook endpoint from the Stripe account first, then the integration with its mappings, for every product. The endpoint is skipped when it's already gone or the key no longer works; otherwise, when it can't be deleted, the integration is kept. The licenses it created stay. Revoke the API key in Stripe afterwards. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = i8Fz4QnRt; // string

try {
    $apiInstance->disconnectIntegration($id);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->disconnectIntegration: ', $e->getMessage(), PHP_EOL;
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

## `getStripeIntegration()`

```php
getStripeIntegration($product_id): \LicenseManager\Model\StripeIntegration
```

Get the Stripe integration of a product

The organization connects one Stripe account for its live products, and one in test mode for its test products. Its mappings tell which Stripe prices create licenses of the product. Doesn't accept tokens: only API keys and sessions.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$product_id = x7Kp2QaZ; // string

try {
    $result = $apiInstance->getStripeIntegration($product_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->getStripeIntegration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |

### Return type

[**\LicenseManager\Model\StripeIntegration**](../Model/StripeIntegration.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listStripePrices()`

```php
listStripePrices($id): \LicenseManager\Model\ListStripePrices200Response
```

List the Stripe prices of an integration

Active one-time prices of active products of the Stripe account, the ones that can be mapped, up to 500. Doesn't accept tokens: only API keys and sessions.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = i8Fz4QnRt; // string

try {
    $result = $apiInstance->listStripePrices($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->listStripePrices: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\ListStripePrices200Response**](../Model/ListStripePrices200Response.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateIntegration()`

```php
updateIntegration($id, $update_integration): \LicenseManager\Model\Integration
```

Update an integration

Changes the settings of the integration, for every product of its mode. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = i8Fz4QnRt; // string
$update_integration = new \LicenseManager\Model\UpdateIntegration(); // \LicenseManager\Model\UpdateIntegration

try {
    $result = $apiInstance->updateIntegration($id, $update_integration);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->updateIntegration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_integration** | [**\LicenseManager\Model\UpdateIntegration**](../Model/UpdateIntegration.md)|  | |

### Return type

[**\LicenseManager\Model\Integration**](../Model/Integration.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateStripeMapping()`

```php
updateStripeMapping($id, $update_integration_mapping): \LicenseManager\Model\IntegrationMapping
```

Change the policy of a mapping

Only affects the licenses created afterwards. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = i8Fz4QnRt; // string
$update_integration_mapping = new \LicenseManager\Model\UpdateIntegrationMapping(); // \LicenseManager\Model\UpdateIntegrationMapping

try {
    $result = $apiInstance->updateStripeMapping($id, $update_integration_mapping);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->updateStripeMapping: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_integration_mapping** | [**\LicenseManager\Model\UpdateIntegrationMapping**](../Model/UpdateIntegrationMapping.md)|  | |

### Return type

[**\LicenseManager\Model\IntegrationMapping**](../Model/IntegrationMapping.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
