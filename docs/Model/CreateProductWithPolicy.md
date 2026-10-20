# CreateProductWithPolicy

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** |  |
**slug** | **string** | Unique within the organization. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional]
**default_policy** | [**\LicenseManager\Model\PolicySettings**](PolicySettings.md) |  | [optional]
**is_test_from_product_id** | **string** | Creates a test product: a sandbox of this live product of the organization, starting with copies of its policies, releases and portal settings. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
