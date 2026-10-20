# UpdateLicense

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**expires_at** | **\DateTime** | &#x60;null&#x60; makes the license never expire. | [optional]
**meta** | **array<string,mixed>** | Free-form JSON object. | [optional]
**max_machines** | **int** | Maximum number of active machines the license can be used on. &#x60;null&#x60; for no limit. | [optional]
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the license, in seconds. At least one hour (&#x60;3600&#x60;). | [optional]
**max_version** | [**\LicenseManager\Model\LicenseMaxVersionInput**](LicenseMaxVersionInput.md) | Latest version of the product the license can use. The values left out are kept. | [optional]
**price** | [**\LicenseManager\Model\PriceInput**](PriceInput.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
