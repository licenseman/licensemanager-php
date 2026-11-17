# ImportLicense

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**email** | **string** | Email of the customer the license belongs to. The product&#39;s customer with this email, compared regardless of case, or a new one when there&#39;s none. |
**key** | **string** | The license&#39;s current key, kept as is. Case sensitive. Starts with &#x60;TEST-&#x60; in test products, which is added when missing, and removed in live products. |
**policy_id** | **string** | Policy of the product the license follows. Defaults to the product&#39;s default policy. | [optional]
**expires_at** | **\DateTime** | &#x60;null&#x60; makes the license never expire. Defaults to the creation date plus the duration of the policy, or &#x60;null&#x60; when the policy has none. | [optional]
**meta** | **array<string,mixed>** | Free-form JSON object. | [optional]
**max_machines** | **int** | Maximum number of active machines the license can be used on. &#x60;null&#x60; for no limit. Defaults to the one of the policy. | [optional]
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the license, in seconds. At least one hour (&#x60;3600&#x60;). Defaults to the one of the policy. | [optional]
**price** | [**\LicenseManager\Model\PriceInput**](PriceInput.md) |  | [optional]
**max_version** | [**\LicenseManager\Model\LicenseMaxVersionInput**](LicenseMaxVersionInput.md) |  | [optional]
**cancellable_until** | **\DateTime** | End of the money back guarantee: until then, the customer can cancel the license from the customer portal, or with a token. &#x60;null&#x60; to not let them. Defaults to the creation date plus the policy&#39;s &#x60;moneyBackGuaranteeDays&#x60;, or &#x60;null&#x60; when it has none. | [optional]
**name** | **string** | Name of the customer, given to it when it has none yet. | [optional]
**subscription** | [**\LicenseManager\Model\ImportLicenseSubscription**](ImportLicenseSubscription.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
