# LicenseManager\ProductsApi



All URIs are relative to https://api.licensemanager.dev, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createProduct()**](ProductsApi.md#createProduct) | **POST** /v1/products | Create a product |
| [**deleteProduct()**](ProductsApi.md#deleteProduct) | **DELETE** /v1/products/{id} | Delete a product |
| [**deleteProductLogo()**](ProductsApi.md#deleteProductLogo) | **DELETE** /v1/products/{id}/logo | Delete a product logo |
| [**getProduct()**](ProductsApi.md#getProduct) | **GET** /v1/products/{id} | Get a product |
| [**getProductStats()**](ProductsApi.md#getProductStats) | **GET** /v1/products/{id}/stats | Get the stats of a product |
| [**listProducts()**](ProductsApi.md#listProducts) | **GET** /v1/products | List products |
| [**resetProduct()**](ProductsApi.md#resetProduct) | **POST** /v1/products/{id}/reset | Reset a test product |
| [**updateProduct()**](ProductsApi.md#updateProduct) | **PATCH** /v1/products/{id} | Update a product |
| [**uploadProductLogo()**](ProductsApi.md#uploadProductLogo) | **PUT** /v1/products/{id}/logo | Upload a product logo |


## `createProduct()`

```php
createProduct($create_product_with_policy): \LicenseManager\Model\Product
```

Create a product

Without a `slug`, the product gets one derived from its name: lower cased, without accents and special characters (`Élan Pro 2!` becomes `elan-pro-2`). When another product of the organization already uses it, a dash and 3 random lowercase letters or digits are appended (`elan-pro-2-k3f`), until the slug is free.  An explicit `slug` is used as is: the request fails with a `409` when it's taken, it's never changed.  Slug uniqueness is enforced by the database, so when concurrent requests end up with the same slug, only one succeeds and the others get a `409`, even without an explicit `slug`. Retrying such a request without a `slug` derives a new one.  The product is created with its default policy, named `Default policy` with the `default` slug, whose settings are given by `defaultPolicy`. Omitted settings default to licenses that never expire, on a single machine, offline for one week, for every version of the product. Unlike `createPolicy`, where `maxMachines` defaults to no limit.  With `isTestFromProductId`, the product is a test product: its id, its slug, and the ids, slugs and license keys of its resources start with `test_` (`TEST-` for license keys), and only test API keys reach it. It starts with copies of the policies, releases and portal settings of the live product, `defaultPolicy` is ignored. Later changes to the live product aren't copied: reset the test product to copy them again. Test API keys can only create test products, live API keys only live ones.  **Required role permission**: `product:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_product_with_policy = new \LicenseManager\Model\CreateProductWithPolicy(); // \LicenseManager\Model\CreateProductWithPolicy

try {
    $result = $apiInstance->createProduct($create_product_with_policy);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->createProduct: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_product_with_policy** | [**\LicenseManager\Model\CreateProductWithPolicy**](../Model/CreateProductWithPolicy.md)|  | |

### Return type

[**\LicenseManager\Model\Product**](../Model/Product.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteProduct()`

```php
deleteProduct($id)
```

Delete a product

Deletes the product along with its policies, customers and releases, and its test products with everything they hold. A live product that licenses belong to can't be deleted: delete them first. A test product can always be deleted, along with its licenses and machines. The events of the deleted policies and licenses can no longer be listed.  **Required role permission**: `product:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = x7Kp2QaZ; // string

try {
    $apiInstance->deleteProduct($id);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->deleteProduct: ', $e->getMessage(), PHP_EOL;
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

## `deleteProductLogo()`

```php
deleteProductLogo($id): \LicenseManager\Model\Product
```

Delete a product logo

Removes the logo of the product, and deletes its image. Succeeds when the product has no logo.  **Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = x7Kp2QaZ; // string

try {
    $result = $apiInstance->deleteProductLogo($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->deleteProductLogo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\Product**](../Model/Product.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProduct()`

```php
getProduct($id): \LicenseManager\Model\Product
```

Get a product

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = x7Kp2QaZ; // string

try {
    $result = $apiInstance->getProduct($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->getProduct: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\Product**](../Model/Product.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getProductStats()`

```php
getProductStats($id): \LicenseManager\Model\ProductStats
```

Get the stats of a product

Counts of the licenses and machines of the product, number of licenses created each day over the last 30 days and each month over the last 12 months, overall and per policy, revenue per currency over the same periods, and successful activations each day over the last 30 days. Days and months are in UTC.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = x7Kp2QaZ; // string

try {
    $result = $apiInstance->getProductStats($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->getProductStats: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\ProductStats**](../Model/ProductStats.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listProducts()`

```php
listProducts($page, $page_size, $sort, $search, $slug, $is_test): \LicenseManager\Model\ProductList
```

List products

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$page = 1; // int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
$page_size = 20; // int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
$sort = -createdAt; // string | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
$search = pro; // string | Case-insensitive text the name or slug contains.
$slug = acme-pro; // string | Only returns the product with this exact slug.
$is_test = false; // string | Only returns the test products with `true`, the live ones with `false`. API keys only list the products of their own mode.

try {
    $result = $apiInstance->listProducts($page, $page_size, $sort, $search, $slug, $is_test);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->listProducts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **string**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;] |
| **search** | **string**| Case-insensitive text the name or slug contains. | [optional] |
| **slug** | **string**| Only returns the product with this exact slug. | [optional] |
| **is_test** | **string**| Only returns the test products with &#x60;true&#x60;, the live ones with &#x60;false&#x60;. API keys only list the products of their own mode. | [optional] |

### Return type

[**\LicenseManager\Model\ProductList**](../Model/ProductList.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `resetProduct()`

```php
resetProduct($id): \LicenseManager\Model\Product
```

Reset a test product

Deletes the customers, licenses, machines, policies and releases of the test product, with their events, then copies the policies, releases and portal settings of its live product again. Its id, name and slug are kept, but the copied policies get new ids. The tokens of its customers, licenses and machines stop working.  **Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = x7Kp2QaZ; // string

try {
    $result = $apiInstance->resetProduct($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->resetProduct: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\LicenseManager\Model\Product**](../Model/Product.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateProduct()`

```php
updateProduct($id, $update_product): \LicenseManager\Model\Product
```

Update a product

A product can't be turned into a test product, or back: `isTestFromProductId` can't be changed.  **Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = x7Kp2QaZ; // string
$update_product = new \LicenseManager\Model\UpdateProduct(); // \LicenseManager\Model\UpdateProduct

try {
    $result = $apiInstance->updateProduct($id, $update_product);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->updateProduct: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_product** | [**\LicenseManager\Model\UpdateProduct**](../Model/UpdateProduct.md)|  | |

### Return type

[**\LicenseManager\Model\Product**](../Model/Product.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `uploadProductLogo()`

```php
uploadProductLogo($id, $file): \LicenseManager\Model\Product
```

Upload a product logo

Replaces the logo of the product, shown in the web app and the customer portal. The previous logo is deleted.  Accepts WebP, PNG, JPEG and SVG images up to 1 MB, recognized by their content. Logos are shown in squares: use square images, 256×256 pixels for bitmaps. The web app crops and resizes images to this size, and converts them to WebP, before uploading them.  **Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: apiKey
$config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = LicenseManager\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new LicenseManager\Api\ProductsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = x7Kp2QaZ; // string
$file = '/path/to/file.txt'; // \SplFileObject | WebP, PNG, JPEG or SVG image, up to 1 MB.

try {
    $result = $apiInstance->uploadProductLogo($id, $file);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ProductsApi->uploadProductLogo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **file** | **\SplFileObject****\SplFileObject**| WebP, PNG, JPEG or SVG image, up to 1 MB. | |

### Return type

[**\LicenseManager\Model\Product**](../Model/Product.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
