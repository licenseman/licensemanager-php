# LicenseManager\PortalApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createPortalLink()**](PortalApi.md#createPortalLink) | **POST** /v1/customers/{id}/portal-links | Create a link to the customer portal |
| [**getPortal()**](PortalApi.md#getPortal) | **GET** /v1/portal/{productId} | Get the customer portal of a product |
| [**requestPortalLink()**](PortalApi.md#requestPortalLink) | **POST** /v1/portal/{productId}/request-link | Email a link to the customer portal |
| [**sendPortalLink()**](PortalApi.md#sendPortalLink) | **POST** /v1/customers/{id}/portal-links/send | Email a link to the customer portal to the customer |


## `createPortalLink()`

```php
createPortalLink($id, $create_portal_link): \LicenseManager\Model\PortalLink
```

Create a link to the customer portal

Link letting the customer see their licenses, cancel them during their money back guarantee, and deactivate their machines in the customer portal, without signing in. Anyone with the link can, until it expires or the customer is deleted: it can't be revoked otherwise. The token also works with the API endpoints that accept customer tokens.  Links can be created while the product's customer portal is disabled, but the portal answers `404` until it's enabled, and `sendPortalLink` refuses to email them.  **Required role permission**: `portalLink:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\PortalApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = c9Wd3RtE; // string
$create_portal_link = new \LicenseManager\Model\CreatePortalLink(); // \LicenseManager\Model\CreatePortalLink

try {
    $result = $apiInstance->createPortalLink($id, $create_portal_link);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PortalApi->createPortalLink: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **create_portal_link** | [**\LicenseManager\Model\CreatePortalLink**](../Model/CreatePortalLink.md)|  | |

### Return type

[**\LicenseManager\Model\PortalLink**](../Model/PortalLink.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPortal()`

```php
getPortal($product_id, $return_url): \LicenseManager\Model\Portal
```

Get the customer portal of a product

Names of the product and of its organization, colors of the customer portal, and link back to the product's website. Answers `404` when the product's customer portal is disabled: with the `portal_disabled` code and the slugs of the product and its organization when signed in as a member of the organization, so they can enable it. Doesn't need authentication.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new LicenseManager\Api\PortalApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$product_id = x7Kp2QaZ; // string
$return_url = https://example.com/account; // string | Link back to your website to show, used when its domain is one of the product's `returnDomains`.

try {
    $result = $apiInstance->getPortal($product_id, $return_url);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PortalApi->getPortal: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **return_url** | **string**| Link back to your website to show, used when its domain is one of the product&#39;s &#x60;returnDomains&#x60;. | [optional] |

### Return type

[**\LicenseManager\Model\Portal**](../Model/Portal.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `requestPortalLink()`

```php
requestPortalLink($product_id, $request_portal_link)
```

Email a link to the customer portal

Emails the customer of the product with this email a link to the customer portal, working for 1 hour. Answers `404` when the product's customer portal is disabled. Answers the same whether the customer exists or not, so the API doesn't tell which emails are customers. Test products only email the members of the organization: the link isn't sent to other customers, with the same answer. Doesn't need authentication.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new LicenseManager\Api\PortalApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$product_id = x7Kp2QaZ; // string
$request_portal_link = new \LicenseManager\Model\RequestPortalLink(); // \LicenseManager\Model\RequestPortalLink

try {
    $apiInstance->requestPortalLink($product_id, $request_portal_link);
} catch (Exception $e) {
    echo 'Exception when calling PortalApi->requestPortalLink: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **product_id** | **string**|  | |
| **request_portal_link** | [**\LicenseManager\Model\RequestPortalLink**](../Model/RequestPortalLink.md)|  | |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendPortalLink()`

```php
sendPortalLink($id, $send_portal_link)
```

Email a link to the customer portal to the customer

Emails a link created with `createPortalLink` to the customer's email. Fails while the product's customer portal is disabled, and, in test products, when the customer's email isn't a member's of the organization: test products only email members, so testing never emails real customers.  **Required role permission**: `portalLink:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\PortalApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = c9Wd3RtE; // string
$send_portal_link = new \LicenseManager\Model\SendPortalLink(); // \LicenseManager\Model\SendPortalLink

try {
    $apiInstance->sendPortalLink($id, $send_portal_link);
} catch (Exception $e) {
    echo 'Exception when calling PortalApi->sendPortalLink: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **send_portal_link** | [**\LicenseManager\Model\SendPortalLink**](../Model/SendPortalLink.md)|  | |

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
